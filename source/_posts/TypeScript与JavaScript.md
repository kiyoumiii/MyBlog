---
title: TypeScript与JavaScript
date: 2025-02-21 22:33:35
categories:
- [前端开发]
tags:
- [前端]
---

# TypeScript与JavaScript

JavaScript 和 TypeScript 是现代前端开发中最常用的两种语言。作为 JavaScript 的超集，TypeScript 提供了对 JavaScript 的增强功能，特别是在类型系统和开发工具支持方面。

### 1. JavaScript
JavaScript（简称 JS）是一种广泛应用于前端开发的动态类型编程语言，最初是由 Netscape 的 Brendan Eich 在 1995 年开发的。它最初的目标是增强网页的互动性，如验证表单、处理用户输入、动态加载内容等。
随着时间的推移，JavaScript 已经发展成一种全栈开发语言，不仅用于浏览器端开发，也广泛应用于服务器端开发（如 Node.js）。

- 动态类型：变量的类型在运行时确定。
- 解释执行：JavaScript 代码在浏览器中直接运行，而无需编译。
- 事件驱动：广泛应用于用户界面的交互。
- 异步编程：支持异步编程（如使用回调函数、Promise 和 async/await）。

JavaScript 是动态类型语言，意味着变量的类型是在运行时确定的。你可以随时改变变量的类型，且没有类型检查。这虽然灵活，但也容易引入错误，尤其是在大型应用中，类型错误可能不容易被发现。

JavaScript 支持面向对象编程，但语法相对简洁且不够严格。例如，JavaScript 中的类是基于原型的，不支持传统的接口和类型检查。

JavaScript 是浏览器的原生语言，直接在浏览器中运行，不需要任何编译步骤。

### 2. TypeScript
TypeScript（简称 TS）是由微软开发的一种编程语言，它是 JavaScript 的超集，意味着 JavaScript 的合法代码也是 TypeScript 的合法代码。TypeScript 增强了 JavaScript 的功能，特别是加入了强类型检查、接口、类等面向对象的特性，以及静态类型系统，可以在编译阶段捕捉到潜在的错误

- 静态类型检查：在编译阶段检查类型错误，提高代码的可靠性。
- 类型推断：即使没有显式声明类型，TypeScript 也会自动推断变量的类型。
- 类和接口：支持面向对象编程，提供类、接口、继承等功能。
- 现代 JavaScript 特性：TypeScript 支持最新的 JavaScript 特性，并且可以编译成兼容旧浏览器的 JavaScript 代码。

TypeScript 加入了静态类型系统，可以在编译阶段进行类型检查，帮助开发者尽早发现错误。TypeScript 不仅支持原始类型（如 string、number、boolean），还支持复杂类型（如数组、元组、枚举、接口、联合类型等）。

TypeScript 在 JavaScript 的基础上增加了类、接口、继承等面向对象的特性，语法更加严格，有助于开发者编写更清晰、可维护的代码。

TypeScript 需要编译成 JavaScript，才能在浏览器或 Node.js 中执行。TypeScript 编译器将 TS 代码转换为 JavaScript 代码，通常目标是 ES5 或 ES6 代码，这样可以兼容各种浏览器和环境。


### 3.代码对比

1. 语法

类型注解

- JavaScript: 不支持类型注解，变量的类型由值来推断。
- TypeScript: 支持静态类型注解，可以在变量、函数参数、函数返回值等地方显式指定类型。

``` typescript
// TypeScript
function add(a: number, b: number): number {
  return a + b;
}

```

类和接口

- JavaScript: 使用原型链来实现对象的继承，没有类和接口的概念。
- TypeScript: 引入了类和接口，支持面向对象的编程风格。

``` typescript
// TypeScript
interface Shape {
  calculateArea(): number;
}

class Circle implements Shape {
  constructor(private radius: number) {}

  calculateArea() {
    return Math.PI * this.radius ** 2;
  }
}

```

枚举

- JavaScript: 不支持枚举类型。
- TypeScript: 支持枚举类型，可以定义一组命名的常量值。

``` typescript
// TypeScript
enum Direction {
  Up,
  Down,
  Left,
  Right,
}

```

类型系统

静态类型检查

- JavaScript: 在运行时进行类型检查，类型错误只会在执行阶段被发现。
- TypeScript: 使用静态类型检查，在编译时进行类型检查，能够提前发现并避免一些潜在的错误。

``` typescript
// TypeScript
let name: string = "Alice";
name = 123; // 编译时错误

```

类型推断

- JavaScript: 变量的类型由值来推断。
- TypeScript: 支持类型推断，当类型没有显式指定时，会根据上下文自动推断出变量的类型。

``` typescript
// TypeScript
let age = 25; // 推断为 number 类型

```

提供更丰富的类型
- JavaScript: 基本数据类型和对象类型。
- TypeScript: 支持基本数据类型、对象类型、元组、联合类型、交叉类型、字面量类型等更丰富的类型。

``` typescript
// TypeScript
type Status = "pending" | "in_progress" | "completed";

interface Fruit {
  name: string;
  color: string;
}

type Apple = Fruit & { type: "apple" };
type Banana = Fruit & { type: "banana" };

function getFruitColor(fruit: Apple | Banana): string {
  return fruit.color;
}

```

工具支持

编辑器支持
JavaScript: 可以在大多数代码编辑器中编辑 JavaScript 代码，但没有针对 JavaScript 的专用编辑器。
TypeScript: 得益于类型系统，TypeScript 在编辑器中提供了更强大的代码补全、类型检查和重构功能。同时，一些编辑器如 Visual Studio Code 提供了针对 TypeScript 的更完善支持。

调试支持
JavaScript: 可以通过浏览器的开发者工具进行调试。
TypeScript: 能够生成可调试的 JavaScript 代码，支持在编辑器或浏览器中进行调试。

文档和社区
JavaScript: 具有成熟的文档和庞大的社区资源，容易找到相关的教程、博客文章和解决方案。
TypeScript: TypeScript 基于 JavaScript，因此可以享受到 JavaScript 社区的一部分资源，此外还有针对 TypeScript 的官方文档、社区论坛和第三方库的支持。

第三方库
JavaScript: 拥有世界上最大的开源生态系统，有众多的第三方库和框架可供选择。
TypeScript: TypeScript 与 JavaScript 兼容，可以直接使用 JavaScript 的第三方库。此外，TypeScript 还有自己的类型声明文件（.d.ts）生态系统，提供了大量的类型定义供开发者使用。

TypeScript编写一个API的案例
下面演示用TypeScript 开发一个简单的 Express.js 后端 API：

``` typescript
import express, { Request, Response } from "express";

interface User {
  name: string;
  age: number;
}

const app = express();

app.use(express.json());

app.post("/users", (req: Request, res: Response) => {
  const user: User = req.body;
  // 处理用户数据
  res.json(user);
});

app.listen(3000, () => {
  console.log("Server is running on port 3000");
});

```

在该案例中，使用 TypeScript 提供的静态类型检查，使你能够更早地发现和解决潜在的错误。此外 TypeScript 还提供了代码补全和类型推断，大大提高开发效率。

性能：
将ts编译为js之后，和原生js的性能表现几乎是一致的