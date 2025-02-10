## ES6面试题

### 说说var. let、const之间的区别

`var` 、 `let` 和 `const` 都是用来在 JavaScript 中声明变量的关键字，但它们在作用域、声明行为和可变性方面有所不同。以下是它们之间主要的区别：

01. **作用域**：
   - `var` ：在ES5及更早版本中， `var` 声明的变量具有函数作用域（函数作用域是指变量在其所在函数体内有效，若不在任何函数内，则属于全局作用域）。
   - `let` 和 `const` ：从ES6开始， `let` 和 `const` 声明的变量具有块级作用域（块级作用域是指变量仅在其所在的任意一对花括号 `{}` 内部有效，比如循环体、条件语句或者函数体内部的独立块）。

02. **变量提升（Hoisting）**：
   - `var` ：变量声明会被提升到其所在的作用域顶部，即使实际声明出现在后面的代码中，也能在整个作用域内访问。但是，赋值操作并不会被提升。
   - `let` 和 `const` ：虽然它们的声明也会被提升，但在其声明前访问会导致“暂时性死区”（Temporal Dead Zone, TDZ），即在声明之前无法访问变量，否则会抛出引用错误。

03. **重复声明**：
   - `var` ：在同一作用域内可以多次声明同一个变量而不报错，只会被视为一个声明。
   - `let` ：在同一作用域内不允许重复声明同一个变量，否则会抛出语法错误。
   - `const` ：也不能在同一作用域内重复声明，且一旦声明，其绑定的变量不得重新声明或重新赋值（不过需要注意的是，对于对象和数组类型的const变量，虽然不能重新赋值，但其内部属性是可以修改的）。

04. **可变性**：
   - `var` 和 `let` ：声明的变量可以被重新赋值。
   - `const` ：声明的是常量，一旦给其赋值后，值不可改变。如果 `const` 用来声明基本类型（如字符串、数字、布尔值），则该变量不可再赋值；如果声明的是对象或数组，尽管其指向的内存地址不可改变，但对象或数组本身的属性或元素是可以改变的。

总结起来：
* `var` 是早期JS的标准变量声明方式，容易导致变量作用域问题和变量提升带来的潜在bug。
* `let` 提供了块级作用域的变量声明，有助于避免变量污染和创建更清晰的作用域边界。
* `const` 适用于声明那些不应该改变的变量，增强了程序的健壮性和可读性，同时也提供了块级作用域的保证。

### ES6中数组新增了哪些扩展?

ES6（ECMAScript 6）为JavaScript数组增加了许多新的API和功能，以下是一些主要的数组扩展：

01. **Array.from()**
   - 将类数组对象或可迭代对象转换为真正的数组，例如：

     

```javascript
     const arrayLike = {
         0: 'a',
         1: 'b',
         length: 2
     };
     const arr = Array.from(arrayLike); // ['a', 'b']
```

02. **Array.of()**
   - 创建一个具有指定元素的新数组，与直接使用构造函数创建数组相比，Array.of()的行为更直观和一致。

     

```javascript
     const arr = Array.of(1, 2, 3); // [1, 2, 3]
```

03. **Array.prototype.copyWithin()**
   - 在数组内部复制一部分到另一部分，替换掉原有值。

     

```javascript
     const arr = [1, 2, 3, 4, 5];
     arr.copyWithin(0, 3); // [4, 5, 3, 4, 5]
```

04. **Array.prototype.find() 和 Array.prototype.findIndex()**
   - find()方法用于查找数组中第一个符合条件的元素，并返回该元素的值。

     

```javascript
     const numbers = [1, 2, 3, 4, 5];
     const foundNumber = numbers.find(num => num > 3); // 4
```

   - findIndex()方法与find()类似，但返回的是找到的元素的索引。

     

```javascript
     const index = numbers.findIndex(num => num > 3); // 3
```

05. **Array.prototype.fill()**
   - 用给定的值填充数组的一部分或全部。

     

```javascript
     const arr = new Array(5).fill(0); // [0, 0, 0, 0, 0]
```

06. **扩展运算符（...）**
   - 用于解构赋值和展开数组。

     

```javascript
     const arr1 = [1, 2, 3];
     const arr2 = [...arr1, 4, 5]; // [1, 2, 3, 4, 5]
```

07. **Array.prototype.entries()、keys() 和 values()**
   - 返回迭代器，分别用于遍历数组的键值对、键和值。

     

```javascript
     for (const [index, value] of arr.entries()) {
         console.log(index, value);
     }
```

08. **Array.prototype.includes()**
   - 判断数组是否包含某个指定的值，如果有则返回true，否则返回false。

     

```javascript
     const arr = [1, 2, 3];
     console.log(arr.includes(2)); // true
```

09. **迭代器（Iterators）与for...of循环**
   - for...of循环可以直接遍历数组或其他可迭代对象的值。

     

```javascript
     for (const num of numbers) {
         console.log(num);
     }
```

以上只是ES6中数组扩展的一部分，还有其他的改进和新增方法，例如 `Array.prototype.keys()` , `Array.prototype.values()` , `Array.prototype.forEach()` , `Array.prototype.some()` , `Array.prototype.every()` , `Array.prototype.reduce()` , `Array.prototype.reduceRight()` 等方法的规范化和标准化。同时，ES6还引入了新的数据结构如Map和Set，它们也有各自的迭代方法。

### 函数新增了哪些扩展?

ES6（ECMAScript 6）对JavaScript函数进行了多项重要的扩展，提升了函数的灵活性和功能性。以下是ES6中函数的一些关键新增特性：

01. **箭头函数（Arrow Functions）**
   

```javascript
   // ES5
   var square = function(x) {
       return x * x;
   };

   // ES6
   const square = (x) => x * x;
```

   箭头函数简化了函数的定义方式，并且没有自己的 `this` 、 `arguments` 、 `super` 、 `new.target` 等上下文关键词，它们从外围作用域继承。

02. **默认参数值**
   

```javascript
   // ES5
   function multiply(a, b) {
       if (typeof b === 'undefined') b = 1;
       return a * b;
   }

   // ES6
   function multiply(a, b = 1) {
       return a * b;
   }
```

   函数参数可以设置默认值，当传入的参数为 `undefined` 时，使用默认值。

03. **剩余参数（Rest Parameters）**
   

```javascript
   // ES5
   function sum() {
       var args = Array.prototype.slice.call(arguments);
       return args.reduce(function(total, num) {
           return total + num;
       }, 0);
   }

   // ES6
   function sum(...numbers) {
       return numbers.reduce((total, num) => total + num, 0);
   }
```

   使用 `...` 操作符可以捕获剩余参数，并将它们收集到一个数组中。

04. **解构参数（Destructuring in Parameters）**
   

```javascript
   // ES6
   function greet({
       name = 'Guest',
       age
   }) {
       console.log(`Hello, ${name}. You are ${age} years old.`);
   }
```

   函数参数可以是对象的解构形式，允许你提取和赋予默认值给对象的属性。

05. **尾调用优化（Tail Call Optimization）**
   ES6规范理论上支持尾递归优化，即在满足特定条件的尾递归调用中，引擎可以避免栈溢出的问题。但实际上，浏览器对尾调用优化的支持情况参差不齐，而且尚未成为强制要求。

06. **函数表达式和`name`属性**
   函数表达式（包括箭头函数）可以拥有 `name` 属性，这对于调试和堆栈跟踪很有帮助。

07. **函数参数的扩展运算符（Spread Syntax）**
   

```javascript
   function add(...args) {
       return args.reduce((total, n) => total + n, 0);
   }
```

   扩展运算符可以用于传递数组或者可迭代对象作为函数参数，将元素展开传入。

08. **函数作用域中的`let`和`const`**
   在函数内部可以使用 `let` 和 `const` 声明变量，它们具有块级作用域，解决了ES5中 `var` 带来的变量作用域和提升问题。

这些特性大大提高了JavaScript中函数的表达力和代码的可读性，并增强了函数在实际编程中的灵活性。

### 对象新增了哪些扩展?

ES6对JavaScript的对象（Object）增加了许多重要且实用的新特性，这里列出了一些主要的扩展：

01. **简写属性名（Shorthand Property Names）**
   

```javascript
   // ES5
   const person = {
       firstName: "John",
       lastName: "Doe"
   };

   // ES6
   const person = {
       firstName,
       lastName
   };
```

   如果变量名与对象属性名相同，可以直接使用变量名作为属性名。

02. **计算属性名（Computed Property Names）**
   

```javascript
   const key = "firstName";
   const person = {
       [key]: "John"
   };
```

   可以使用方括号 `[]` 包裹表达式来动态生成属性名。

03. **方法的简写（Method Shorthand）**
   

```javascript
   // ES5
   const person = {
       sayName: function() {
           console.log(this.firstName + " " + this.lastName);
       }
   };

   // ES6
   const person = {
       sayName() {
           console.log(this.firstName + " " + this.lastName);
       }
   };
```

   可以省略 `function` 关键字来定义对象的方法。

04. **对象字面量扩展运算符（Object Literal Spread Syntax）**
   

```javascript
   const defaults = {
       logLevel: 1
   };
   const options = {
       ...defaults,
       logLevel: 2,
       debug: true
   };
```

   使用扩展运算符 `...` 可以合并多个对象，源对象的属性会被复制到目标对象中。

05. **Object.assign()**
   

```javascript
   const target = {
       a: 1
   };
   const source1 = {
       b: 2
   };
   const source2 = {
       c: 3
   };
   Object.assign(target, source1, source2);
```

`Object.assign()` 方法可以用于浅拷贝对象属性，将源对象的属性复制到目标对象中。

06. **Object.is()**
   

```javascript
   console.log(Object.is(NaN, NaN)); // true
```

`Object.is()` 方法用来比较两个值是否严格相等，与 `===` 操作符相比，它对NaN和+0/-0做了特殊处理。

07. **Object.keys(), Object.values(), Object.entries()**
   

```javascript
   const obj = {
       a: 1,
       b: 2,
       c: 3
   };
   console.log(Object.keys(obj)); // ["a", "b", "c"]
   console.log(Object.values(obj)); // [1, 2, 3]
   console.log(Object.entries(obj)); // [["a", 1], ["b", 2], ["c", 3]]
```

   这三个方法分别返回对象的所有属性名数组、属性值数组以及键值对组成的数组。

08. **Proxy对象**
   Proxy对象可以用来创建一个对象的代理，它可以拦截并改变对象的操作行为，实现诸如数据验证、监控、虚拟化等多种功能。

09. **Reflect对象**
   Reflect对象提供了对JavaScript操作对象的反射API，提供了与Proxy对象互补的能力，使得对象操作更易控制和理解。

这些特性极大地丰富了JavaScript对象的使用方式，使得代码更加简洁和易读，同时增强了对象操作的灵活性。

### 你是怎么理解ES6中Promise的? 使用场景?

在ECMAScript 6（ES6）中，Promise 是一种用于解决 JavaScript 中异步编程复杂性的内置对象。Promise 代表了一个现在、将来或永远可能可用，也可能不可用的值。它提供了一种更好的处理异步操作的方式，特别是那些具有不确定完成时间的操作，例如网络请求、定时器事件等。

**理解Promise**

01. **状态和决议过程**：
   - Promise 有三种状态：pending（进行中）、fulfilled（已成功）和rejected（已失败）。一旦Promise被resolve或reject，状态就不能再改变。
   - 当异步操作成功完成时，会调用resolve函数并将结果传递给后续的then链；如果操作失败，则调用reject函数并传递错误。

02. **实例化**：
   创建一个新的Promise通常通过调用Promise的构造函数，传入一个执行器函数，这个函数接收两个参数：resolve和reject，分别用于异步操作成功和失败时通知Promise状态变化。

```javascript
let promise = new Promise((resolve, reject) => {
    // 异步操作...
    if ( /* 操作成功 */ ) {
        resolve(value); // 成功时调用resolve，value是成功的返回结果
    } else {
        reject(error); // 失败时调用reject，error是失败的原因
    }
});
```

03. **链式调用**：
   - Promise支持 `.then` 方法，用于指定当Promise成功时的回调函数，还可以通过 `.catch` 或 `.then(null, rejectHandler)` 处理错误。
   - `.then` 方法返回一个新的Promise，允许连续异步操作构成一个异步操作链。

**使用场景**

* **网络请求**：封装XMLHttpRequest或Fetch API调用，确保请求完成后能够正确处理结果或错误。
   

```javascript
fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));
```

* **资源加载**：加载图片或其他资源，等待加载完成后再进行下一步操作。

```javascript
const loadImage = src => new Promise((resolve, reject) => {
    const img = new Image();
    img.onload = () => resolve(img);
    img.onerror = reject;
    img.src = src;
});

loadImage('/path/to/image.jpg')
    .then(image => document.body.appendChild(image));
```

* **避免回调地狱**：在多层异步操作中，Promise可以帮助构建更易于理解和维护的代码结构，而不是嵌套的回调函数。

* **处理并发和依赖**：通过Promise.all、Promise.race以及手动链接Promise，可以控制多个异步任务之间的并发执行和顺序依赖。

总的来说，Promise 提供了一种更优雅的方式来管理复杂的异步逻辑，使代码更清晰、更具可读性和可维护性。随着ES8引入async/await语法，基于Promise的异步编程变得更加直观和简洁。

### 你是怎么理解ES6中Module的? 使用场景?

在ECMAScript 6（ES6）中，Module（模块）是为了解决JavaScript长期以来缺乏标准模块化机制的问题而引入的重要特性。它允许我们将代码分割成多个可重用的模块，每个模块都有自己独立的作用域，可以导出公共接口，同时导入其他模块的公开接口。

**理解ES6 Module**

01. **导出（Export）**
   - 在一个模块中，我们可以使用 `export` 关键字声明导出成员，可以是一个变量、函数或类。例如：

     

```javascript
     // 导出单个成员
     export const PI = 3.14;

     // 导出多个成员
     export const name = 'World';
     export function greet() {
         ...
     }

     // 导出默认成员（一个模块只能有一个默认导出）
     export default function myFunction() {
         ...
     }
```

02. **导入（Import）**
   - 在另一个模块中，我们可以使用 `import` 关键字来导入其他模块导出的成员。导入可以是默认导入或命名导入。

     

```javascript
     // 默认导入
     import myFunction from './myModule';

     // 命名导入
     import {
         PI,
         name,
         greet
     } from './mathModule';

     // 导入并重命名
     import {
         PI as piValue,
         name as moduleName
     } from './mathModule';
```

03. **静态分析**
   - ES6模块的一个关键特点是静态分析，这意味着模块之间的依赖关系在编译阶段就可以确定，有利于代码优化和打包工具的处理。

**使用场景**

* **代码分割和重用**：将大型项目分解为多个模块，每个模块负责一部分功能，便于代码管理和复用。

* **模块间依赖管理**：通过`import`和`export`，明确模块之间的依赖关系，避免全局命名空间污染。

* **包管理**：与npm（Node Package Manager）等包管理工具结合，可以方便地共享和管理第三方库。

* **按需加载和动态导入**：在某些场景下，可以通过`import()`动态加载模块，实现按需加载，提高首屏加载速度。

* **模块树 shaking**：在构建工具如Webpack中，可以利用模块的静态特性去除未使用的代码，减小最终bundle体积。

总之，ES6 Modules 提供了一种结构化的、标准化的方式来组织和共享JavaScript代码，这对于构建大型和复杂的应用程序至关重要，特别是在现代前端工程化环境中。

### 你是怎么理解ES6中Generator的? 使用场景?

ES6（ECMAScript 6）中的Generator（生成器）是一种特殊的迭代器生成函数，它允许函数在执行过程中保存内部状态，并通过 `yield` 关键字暂停和恢复执行。Generator函数的定义使用了 `function*` 语法，每次调用 `.next()` 方法时，Generator函数会从上次离开的地方继续执行直到遇到下一个 `yield` 表达式，此时函数再次暂停并返回一个包含当前值和完成状态的对象。

**理解Generator：**

01. **定义与执行：**
   

```javascript
   function* gen() {
       let first = yield 'start';
       console.log(first);
       let second = yield 'processing ' + first;
       return 'end ' + second;
   }

   const iterator = gen(); // 创建迭代器
   console.log(iterator.next()); // {value: "start", done: false}
   iterator.next('hello'); // 输出 "hello"，{value: "processing hello", done: false}
   iterator.next('world'); // 输出 "end world"，{value: undefined, done: true}
```

02. **特点：**
   - 可暂停执行：Generator函数可以像中断点一样在执行过程中暂停，并在之后恢复执行。
   - 保留状态：通过 `yield` 表达式，生成器可以在暂停时记住上下文状态，并在下次调用时恢复。
   - 生成器是迭代器工厂：调用Generator函数不会立即执行函数体，而是返回一个迭代器对象，通过调用该迭代器的 `.next()` 方法来逐步驱动函数执行。

**使用场景：**

* **异步编程**：Generator结合`async/await`或Thunk函数可以简化异步代码的编写，实现同步代码风格的异步流程控制。
   

```javascript
   async function main() {
       const result1 = await fetchSomeDataAsync();
       const result2 = yield anotherAsyncTask(result1);
       // ...
   }

   // 或者配合co库等辅助工具
   const co = require('co');
   co(function*() {
       const result1 = yield someAsyncAction();
       const result2 = yield anotherAsyncAction(result1);
   });
```

* **数据流处理**：在处理大量数据时，Generator可以逐次产出数据，避免一次性加载所有数据导致的内存压力。
* **游戏开发**：在游戏循环中，生成器可以方便地控制不同帧的逻辑执行。
* **复杂控制流**：对于需要在循环、条件分支等复杂逻辑中进行暂停和恢复的场景，生成器提供了便利。

总之，Generator是ES6中一个重要特性，它为JavaScript带来了更强大的控制流程能力，尤其在异步编程领域产生了深远影响。随着 `async/await` 的普及，Generator在处理异步任务方面的直接应用有所减少，但它仍然是实现迭代器和其他高级控制流模式的强大工具。

### 你是怎么理解ES6中Decorator的? 使用场景?

在ES6（ECMAScript 6）中，Decorator（装饰器）是一种特殊类型的声明，它允许我们修改类的行为或其属性和方法的元数据，从而在不更改原有类结构的前提下向类添加额外的功能或修改现有功能。装饰器本质上是一个表达式，它能够在编译时被调用，接收被装饰的类（或类的方法）作为参数，并返回一个新的修改过的类（或代理）。

**理解Decorator：**

01. **基本形式：**
   装饰器以 `@decoratorName` 的形式出现在类声明之前或者类的方法声明前，例如：
   

```javascript
   @decorator
   class MyClass {
       constructor(...) {
           ...
       }

       @anotherDecorator
       method() {
           ...
       }
   }
```

   在这里， `@decorator` 是一个装饰器函数，会在类定义时被调用，并且有机会修改或增强 `MyClass` 的行为。

02. **工作原理：**
   装饰器函数通常接受三个参数（尽管不是强制的），对应于装饰的目标：
   - `target` : 被装饰的类的构造函数。
   - `name` : 若装饰的是类的属性或方法，则为属性或方法的名字。
   - `descriptor` : 当装饰类成员时，它是属性或方法的描述符对象。

   装饰器函数可以根据这些参数来修改类的行为，比如添加静态或实例属性，包装方法，或者在类的生命周期钩子中注入额外逻辑。

**使用场景：**

* **权限控制**：装饰器可以用来验证用户权限，确保只有特定用户才能访问某些类方法。
* **日志记录**：在类或方法上应用装饰器，以便自动记录调用日志。
* **缓存**：用于方法级别的缓存，当同一方法被多次调用时，装饰器可以存储结果以提高性能。
* **数据校验**：对类属性进行类型检查或其他验证规则，确保符合预期的数据格式。
* **框架集成**：在Web框架中，装饰器常用于路由定义、中间件注册、模型字段注解等。
* **AOP（面向切面编程）**：通过装饰器实现横切关注点的统一管理，如事务处理、异常处理等。

值得注意的是，虽然装饰器的概念在ES6中提出，但标准尚未正式纳入规范。目前，装饰器提案仍在TC39的Stage中推进，部分TypeScript已支持装饰器的实验性使用，并且可以通过Babel等转译工具将其转换为兼容ES5的代码，在实际项目中得以应用。

### 你是怎么理解ES6新增Set、 Map两种数据结构的?

在ECMAScript 6（ES6）中，新增了两种内置的数据结构：Set和Map，它们是为了弥补JavaScript原有数据结构的不足，提供更高效和独特的数据处理方式。

**Set（集合）**：
Set是一种特殊的类型，它类似于数组，但不允许重复元素。在Set中，所有的元素都是唯一的，无论它们是如何插入的。Set提供了一种方便的方法来追踪一组唯一值，无需开发者手动去重。

* **特性**：
  + 唯一性：Set中的元素都是唯一的，即使插入重复值，集合也不会保存多余的副本。
  + 操作方法：提供了`add()`添加元素、`delete()`删除元素、`has()`检查是否存在某个元素、`clear()`清空集合、以及`forEach()`遍历元素等方法。
  + 遍历：可以使用`for...of`循环直接遍历Set中的所有元素。

**Map（映射）**：
Map是另一种新的数据结构，它允许存储键值对（key-value pairs），每个键必须是唯一的。与JavaScript原有的对象不同，Map中的键不仅可以是字符串，还可以是任何类型的值（包括对象和函数）。

* **特性**：
  + 键值对存储：Map中的每一个元素都是一个键值对，键和值都可以是任意类型。
  + 易于操作：提供了`set(key, value)`添加或更新键值对、`get(key)`获取键对应的值、`delete(key)`删除键值对、`has(key)`检查是否存在某键、`clear()`清空Map、以及`forEach()`遍历所有键值对等方法。
  + 遍历：可以使用`for...of`配合`entries()`、`keys()`或`values()`方法遍历Map。

这两种数据结构在JavaScript中为开发者提供了更强大和灵活的数据处理能力，不仅提高了代码的可读性和简洁性，也解决了原有数据结构无法有效处理的一些场景，比如快速检查元素是否存在（无需反复遍历数组或担心对象属性覆盖问题）、以及处理非字符串键值对等问题。在大规模数据处理、数据去重、关联数据存储等场景下尤为有用。

### 你是怎么理解ES6中Proxy的? 使用场景?

ES6（ECMAScript 6）中的 `Proxy` 是一种内置对象，它提供了一种自定义行为的方式来操作对象。Proxy可以视为目标对象（target object）的代理，对外界访问目标对象的操作进行拦截和定制处理。通过Proxy，开发者可以监控和控制对目标对象的所有访问，包括读取、设置属性、调用方法、以及执行其他操作，如 `in` 、 `delete` 等。

**理解Proxy：**

* **构造函数**：
  Proxy是通过构造函数创建的，接受两个参数：目标对象（target）和处理器对象（handler）。

```javascript
let target = {};
let handler = {
    get(target, propKey, receiver) {},
    set(target, propKey, value, receiver) {},
    // ... 其他各种陷阱方法
};
let proxy = new Proxy(target, handler);
```

* **处理器对象（Handler）**：
  处理器对象定义了一系列被称为“陷阱”（traps）的方法，这些方法会在目标对象上执行相应的操作时被调用。例如， `get` 陷阱会在读取属性时被调用， `set` 陷阱会在设置属性时被调用。

**使用场景：**

01. **数据验证**：
   在设置对象属性时，Proxy可以用于验证输入值的有效性，确保对象保持正确的内部状态。

02. **对象监视**：
   通过Proxy可以监听对象的所有操作，用于日志记录、性能监控等场景。

03. **访问控制**：
   对于敏感属性，Proxy可以拦截访问请求，实现访问权限控制。

04. **虚拟代理**：
   例如，当资源还未加载完成时，可以用一个代理对象来模拟真实资源的行为，当资源加载完毕后，再将代理对象指向真实的资源。

05. **数据绑定和反应式编程**：
   在Vue3等现代前端框架中，Proxy被用于实现高效的响应式数据系统，当对象属性发生变化时，可以自动触发视图更新。

06. **缓存代理**：
   为对象提供缓存功能，如当读取某个属性时，若缓存中有该属性的值，则返回缓存值而非直接访问原对象。

07. **API代理**：
   在服务端或客户端，可以创建一个Proxy来包装API调用，实现统一错误处理、请求计数、过期重试等功能。

总之，Proxy是一个极其强大的工具，它使得开发者能够深入到对象操作的核心层面，实现了对JavaScript对象底层行为的细粒度控制和定制。
