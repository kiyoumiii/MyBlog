---
title: DeepSeek的流式输出：web端与小程序端
date: 2025-03-05 17:27:28
categories:
- [前端开发]
tags:
- [前端开发]
---

Web端很容易实现，但是小程序端会有些特殊。

对于DeepSeek的API，用Python去调用输出时，只要设置stream=True，就可以实现流式输出了：

``` python
response = client.chat.completions.create(
    model="deepseek-chat",
    messages=[
        {"role": "user", "content": "详细介绍一下你自己"},
    ],
    stream=True
)
for chunk in response:
    print(chunk.choices[0].delta.content, end='', flush=True)

```

在 SpringBoot 中实现流式输出可以使用 Sse（Server-SentEvents，服务器发送事件）技术来实现，它是一种服务器推送技术，适合单向实时数据流，我们使用 SpringMVC（基于Servlet）中的SseEmitter对象来实现流式输出。前端接受数据流，只需要创建一个 EventSource 对象，监听后端 SSE 接口，然后将接收到的数据流展示出来即可。


``` javascript
// 流式处理
  const eventSource = new EventSource(`/ai/generateStream?message=` + message);
  eventSource.onmessage = function (event) {
  botMessage.find('.text').append(event.data);  // 追加到机器人消息内容区
  };
  
```


微信小程序基础库从 3.7.1 版本开始内置了云开发 AI+ 能力，开发者可以直接通过小程序中的 wx.cloud.extend.AI 调用。

微信小程序提供了wx.request方法，用于向服务器发起请求并获取数据。

### 一、对于流式接口，我们可以在请求的options中设置stream参数为true，从而启用流式传输。

简单例子：

```js
wx.request({
  url: 'https://example.com/stream', // 流式接口的URL
  method: 'GET',
  responseType: 'stream', // 设置为stream以接收流式数据
  success: function (res) {
    const reader = res.data[0].getReader() // 获取读取器对象
    const readChunk = () => {
      reader.read().then(({ done, value }) => {
        if (done) {
          console.log('Stream finished')
          return
        }
        const data = value.toString() // 将二进制数据转换为字符串
        console.log(data) // 输出数据
        readChunk() // 递归调用，继续读取下一块数据
      })
    }
    readChunk() // 开始读取流式数据
  }
})
```

通过设置responseType为stream来告诉微信小程序我们希望接收流式数据。

在成功回调函数中，我们通过res.data[0].getReader()获取读取器对象，然后使用read方法逐块读取数据。

当读取完成时，我们输出’Stream finished’。需要注意的是，由于流式数据是逐块传输的，因此我们需要使用递归的方式来持续读取下一块数据。

### 二、调用火山方舟中的DeepSeek的流式输出实现实例：

``` javascript
const requestTask=wx.request({
	method: 'POST',
	url: 'https://ark.cn-beijing.volces.com/api/v3/chat/completions',
	header: {
		'Content-Type': 'application/json', 
		'Authorization': 'Bearer API Key'  //Authorization值为“Bearer API Key”
	},
	data: {
		"model": "xxx",	//model值为接入点ID（model）
		"messages": [{
			"role": "user",
			"content": "你是DeepSeek模型吗？",
		}],
        stream: true,   //是否以流的形式输出生成的内容
	},
    enableChunked: true    //开启transfer-encoding chunked
});
 
requestTask.onChunkReceived(res => {
    //在微信开发者工具和真机上接收到的对象格式是不同的，以下代码是针对不同格式进行解码处理
	let type=Object.prototype.toString.call(res.data);
	let text;
	if(type ==="[object Uint8Array]")
		text=decodeURIComponent(escape(String.fromCharCode(...res.data)))
	if(type ==="[object ArrayBuffer]"){
		let uint8Array = new Uint8Array(res.data);
		text=decodeURIComponent(escape(String.fromCharCode(...uint8Array)))
	}
    //将解码后的文本分割成字符串数组，数组中的每个元素就是即时接收到的流式文本
	let list = text.split('\n');
	for (var i = 0; i < list.length; i++) {
		if (list[i]) {
			if (list[i].trim().search(/^data.*\}$/) > -1) {    //过滤掉空行和其他不规则数据行
				let delta = JSON.parse(list[i].substring(6)).choices[0].delta;
                //如果开启了“深度思考”，返回的对象中delta.reasoning_content为深度思考内容，
                //delta.content为主体应答内容
				let content = delta.reasoning_content ? delta.reasoning_content : delta.content;
				console.log(content);
			}
			if (list[i] == 'data: [DONE]') {
				requestTask.abort();
			}
		}
	}
});
```

解析：

- 通过 wx.request 发送一个 POST 请求，请求体包含聊天模型的配置和用户输入。

- 开启流式传输（stream: true），以分块（chunked）形式接收响应数据。

- 使用 onChunkReceived 监听流式数据的接收，并对接收到的数据进行解码和处理。

- 解析流式数据中的 JSON 对象，提取模型生成的内容并输出到控制台。

接收到的数据块，可能是 Uint8Array 或 ArrayBuffer 格式。如果res.data 是 ArrayBuffer格式，先转换为 Uint8Array，再转换为字符串。


P.S.Uint8Array 和 ArrayBuffer 是 JavaScript 中用于处理二进制数据的两种常见格式。

- ArrayBuffer 是一个底层的二进制数据容器，而 Uint8Array 是对 ArrayBuffer 的一种视图，用于以字节为单位访问和操作数据。两者可以相互转换。