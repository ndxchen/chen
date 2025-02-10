## js面试题

### 说说JavaScript中的数据类型? 存储上的差别?

JavaScript 中的数据类型分为两种主要类型：基本数据类型（Primitive Data Types）和引用数据类型（Reference Data Types）。1. 基本数据类型（Primitive Data Types）：
* Number：表示数值类型，可以存储整数和浮点数，存储在栈内存中，直接存储值。 

> 如：let age = 30; 或 let pi = 3.14; 

* String：表示字符串类型，也是存储在栈内存中，直接存储值。字符串是不可变的，一旦创建，修改字符串会创建一个新的字符串对象。

> 如：let name = "Alice"; 

* Boolean：表示布尔类型，只有两个值 true 和 false，存储在栈内存中。 

> 如：let isDone = false; 

* Null：表示一个空或者无意义的值，只有一个值 null，存储在栈内存中。

> 如：let nothing = null; 

* Undefined：表示未定义的值，当声明但未初始化变量时，或者尝试访问不存在的对象属性时，值为 undefined，存储在栈内存中。

> 如：let someVar; // someVar 的值为 undefined

* 自ES6起，还引入了 Symbol 类型，它是唯一的不可变数据类型，也是基本类型之一。
* BigInt（ES2020新增）：表示任意精度的整数，存储在栈内存中，与Number类型不同，它可以存储超过JavaScript Number类型最大安全整数范围的数值。2. 引用数据类型（Reference Data Types）：
* Object：包括但不限于Array（数组）、Function（函数）、Date（日期）、RegExp（正则表达式）等，它们不是直接存储值，而是存储在堆内存中的对象的引用地址。栈内存中存储的是指向堆内存中实际对象的指针。 

> 如：let obj = {name: "Bob"}; 或 let arr = [1, 2, 3]; 

* 对于数组和函数而言，尽管它们的内容（元素或函数体）存储在堆内存中，但引用地址（指针）仍然在栈内存中。在内存存储上的差别主要体现在：

#### 总结

* 基本数据类型：存储空间固定，存储的是值本身，可以直接复制和传递，改变一个变量不会影响另一个变量（除非是通过引用传递基本类型到函数中）。
* 引用数据类型：存储空间不固定，存储的是指向堆内存中对象的地址，复制或传递的是地址，多个变量可以指向同一个对象，对一个对象进行修改会影响到所有指向该对象的变量。

### DOM常见的操作有哪些?

DOM（Document Object Model，文档对象模型）常见的操作包括但不限于以下几种：
01. 查找/查询节点：
  + getElementById(id): 通过ID获取一个元素。
  + getElementsByClassName(className): 获取具有指定类名的所有元素集合。
  + getElementsByTagName(tagName): 获取指定标签名的所有元素集合。
  + querySelector(selector): 根据CSS选择器获取第一个匹配的元素。
  + querySelectorAll(selector): 根据CSS选择器获取所有匹配的元素集合。
02. 修改节点信息：
  + innerHTML: 设置或获取元素内的HTML内容。
  + textContent: 设置或获取元素内的纯文本内容。
  + setAttribute(name, value): 为元素设置属性值。
  + removeAttribute(name): 删除元素的属性。
  + style.property: 直接修改元素样式属性（如 element.style.color = 'red'）。
03. 创建和插入节点：
  + createElement(tagName): 创建一个新的元素节点。
  + createTextNode(text): 创建一个包含文本的文本节点。
  + appendChild(node): 向元素的子节点列表末尾添加新的子节点。
  + insertBefore(newNode, referenceNode): 在参考节点前面插入新的节点。
  + replaceChild(newNode, oldNode): 替换元素中的一个子节点。
04. 删除节点：
  + removeChild(node): 从元素的子节点列表中删除指定的子节点。
05. 遍历和导航节点：
  + childNodes: 返回元素的子节点集合。
  + firstChild/lastChild: 获取元素的第一个或最后一个子节点。
  + parentNode: 获取当前元素的父节点。
  + nextSibling/previousSibling: 获取当前元素的下一个或上一个兄弟节点。
06. 事件处理：
  + addEventListener(type, listener, options): 为元素添加事件监听器。
  + removeEventListener(type, listener, options): 移除已添加的事件监听器。
07. DOM属性操作：
  + dataset: 访问和修改HTML5 data-*属性。
  + classList: 用于操作元素类名的方法集合。
08. DOM遍历方法：•querySelectorAll: 遍历符合CSS选择器的所有节点。
  + forEach: （结合NodeList或HTMLCollection）遍历节点集合。以上是一些常用的DOM操作，它们构成了操作HTML文档的基础，使得开发者可以通过JavaScript动态修改和交互网页内容。

### 说说你对BOM的理解, 常见的BOM对象你了解哪些?

BOM全称Browser Object Model（浏览器对象模型），它是由一系列对象构成的标准，这些对象使得JavaScript能与浏览器进行交互，从而控制浏览器窗口、处理浏览器历史、获取用户代理信息、获取屏幕尺寸等浏览器特有的功能。BOM并非ECMAScript规范的一部分，而是由各种浏览器厂商根据各自的实现来提供一套接口，尽管大部分主流浏览器在BOM方面有相似的实现。常见的BOM对象包括但不限于以下几种：
01. window对象：
  + BOM的核心对象，代表浏览器的主窗口，所有的全局变量和函数都在其作用域下。
  + 提供了许多方法和属性，如alert()、prompt()、confirm()、setTimeout()、setInterval()、clearTimeout()、clearInterval()等。
  + 控制窗口操作的方法，如moveBy()、moveTo()、resizeBy()、resizeTo()等。
02. document对象：
  + 代表整个HTML文档，是DOM（Document Object Model）的主要入口点，用于操作HTML和XML文档内容。
  + 提供了获取和修改文档内容、结构和样式的接口，如getElementById()、getElementsByTagName()、querySelector()、querySelectorAll()等。
03. location对象：
  + 代表当前页面的URL信息，可以通过它改变或获取当前页面的URL地址。
04. navigator对象：
  + 提供了浏览器的信息，如用户代理、插件信息、Cookies是否启用等。
05. history对象：
  + 用于管理浏览器的历史记录，可以通过history.back()、history.forward()、history.go()等方法控制页面跳转。
06. screen对象：
  + 用于获取用户的显示器信息，如屏幕宽度、高度、颜色深度等。
07. event对象：
  + 虽然event对象主要在DOM事件处理中使用，但它是由BOM提供的，用于封装事件相关信息，如事件类型、触发事件的元素、事件处理函数等。
08. frame和frames集合：
  + 如果页面包含框架(frame)，则可以通过frame对象及其集合访问和控制各个框架窗口。这些对象共同构成了JavaScript与浏览器互动的基础，让JavaScript得以实现动态网页、用户交互响应等功能。

### typeof 与instanceof区别?

`typeof` 与 `instanceof` 是 JavaScript 中用于检测变量类型或对象类型的两个操作符，它们的主要区别在于其功能和应用场景的不同：

**typeof**
* `typeof` 是一个一元操作符，用于确定变量或表达式的类型，并返回一个表示类型名称的字符串。
* 它能识别的基本类型包括：`"number"`、`"string"`、`"boolean"`、`"undefined"`、`"bigint"`、`"symbol"`、`"function"`。
* 当应用于对象时，除了`null`之外的对象都会返回 `"object"`，即使这个对象是一个数组或者函数对象。而对于`null`，`typeof null`会返回 `"object"`，这是一个历史遗留问题而不是实际类型。
* 例子：
   

```javascript
   typeof 123; // "number"
   typeof "hello"; // "string"
   typeof true; // "boolean"
   typeof undefined; // "undefined"
   typeof Symbol(); // "symbol"
   typeof null; // "object" (虽不准确，但实际上应为"null")
   typeof []; // "object" (实际上是Array类型)
   typeof {}; // "object" (实际上是Object类型)
   typeof

   function() {}; // "function"
```

**instanceof**
* `instanceof` 是一个二元操作符，用于判断一个对象是否为另一个构造函数的实例。
* 它返回一个布尔值，如果左侧对象是右侧构造函数的实例，则返回 `true`，否则返回 `false`。
* 通过 `instanceof` 可以精确判断对象的具体类型，比如区分出数组、日期对象、正则表达式对象等，这是 `typeof` 无法做到的。
* 例子：
   

```javascript
   var arr = [];
   arr instanceof Array; // true
   new Date() instanceof Date; // true
   {}
   instanceof Object; // true (所有对象都继承自Object)
   function MyConstructor() {}
   var myInstance = new MyConstructor();
   myInstance instanceof MyConstructor; // true
```

总结来说， `typeof` 更侧重于获取变量的基础类型，对于对象仅粗略地区分为“对象”类型；而 `instanceof` 则用于检测对象实例与类或构造函数之间的关系，能够进行更精细的类型判断。

### JavaScriptl原型, 原型链? 有什么特点?

JavaScript 中的原型和原型链具有以下几个主要特点：

01. **所有对象都有原型**：
   - 在 JavaScript 中，每个对象（除了 `null` ）都有一个内部属性 `[[Prototype]]` （可以通过 `__proto__` 或 `Object.getPrototypeOf()` 访问），它指向创建该对象的构造函数的原型对象。
   - 构造函数通过 `.prototype` 属性关联到一个原型对象。

02. **原型链机制**：
   - 当试图访问一个对象的属性时，如果该对象自身没有这个属性，JavaScript 会自动沿着原型链向上查找，即从该对象的原型对象开始，逐级向上搜索直到达到原型链的顶端（通常为 `Object.prototype` ，最终为 `null` ）。

03. **继承与共享**：
   - 原型链实现了对象间的继承，子对象可以从父对象（原型）那里继承属性和方法。
   - 共享特性意味着多个对象实例通过原型链可以共享同一组方法定义，从而节省内存。

04. **动态性**：
   - 原型对象及其属性和方法可以在运行时动态添加或删除，对原型对象的修改会影响到所有关联的实例。

05. **注意点**：
   - 如果在原型上定义了一个可变对象（如数组或对象）作为属性，所有实例都将共享此引用。这意味着，一个实例修改了该共享属性，其他所有实例也能看到这一变化。

06. **链式查找**：
   - 查找过程遵循链式原则，引擎会在原型链上递归地寻找请求的属性或方法，直至找到或抵达原型链的终点。

07. **constructor 属性**：
   - 原型对象上有一个 `constructor` 属性，它指向最初创建该原型的构造函数，这样就形成了构造函数与其原型及其实例间的联系。

综上所述，原型和原型链是 JavaScript 中实现对象继承和属性查找的核心机制，它体现了语言的面向对象设计思想，但又不同于传统的类继承模型，具有自身的独特性和灵活性。

### 说说你对作用域链的理解

JavaScript 中的作用域链（Scope Chain）是一种机制，用于确定在当前执行上下文中如何查找变量和其他资源的位置。作用域链是JavaScript引擎在解析和执行代码时用来决定变量访问权的关键组件之一，它确保了JavaScript的词法作用域规则得以正确执行。

具体来说：

01. **作用域链的概念**：
   - 每个函数在被调用时，都会创建一个新的执行上下文，其中包含一个作用域链，作用域链是一个由多个作用域组成的列表或链式结构。
   - 这个链的前端始终是当前执行上下文的变量对象（活动对象，在函数上下文中，或者全局对象在全局上下文中），然后链接到外部函数的变量对象，以此类推，直到全局作用域为止。

02. **作用域链的形成**：
   - 函数的作用域链在其定义时刻就已经决定好了，而不是在函数调用时。也就是说，函数的作用域链取决于函数被声明时所在的作用域环境。
   - 当函数被调用时，新创建的执行上下文会将其作用域链设置为当前作用域链，并且在其前端插入一个新的变量对象（活动对象）。

03. **作用域链的工作机制**：
   - 当代码尝试访问一个变量时，JavaScript引擎会从当前执行上下文的作用域链的顶部（即当前活动对象）开始向下遍历链中的各个作用域。
   - 如果在当前作用域找不到所需的变量，引擎会继续查找下一个链上的作用域，直到找到该变量或到达全局作用域（链的末尾）。如果全局作用域仍然没有找到，则会导致 `ReferenceError` 异常。

04. **闭包与作用域链**：
   - 闭包是作用域链的一个重要应用，当一个内部函数可以访问并记住其外部函数作用域中的变量时，即使外部函数已经执行完毕，这个内部函数仍保持对外部作用域的引用，这就是闭包现象。因此，即使在外部函数上下文结束之后，其内部函数依然可以通过作用域链访问那些原本应该释放的变量。

总结起来，JavaScript的作用域链保证了变量访问的有效性和安全性，它是实现变量隔离、函数私有变量以及闭包等特性的基础机制。通过作用域链，JavaScript实现了静态作用域（词法作用域），即基于源代码的结构而非程序执行时的状态来决定变量可见性。

### 谈谈this对象的理解

`this` 关键字在 JavaScript 中是一个非常重要的概念，它的行为和指向根据函数调用上下文的不同而有所变化。以下是关于 `this` 的理解要点：

01. **全局作用域中的 this**：
   - 在全局作用域中（不在任何函数内部）， `this` 默认指向全局对象（在浏览器环境中是 `window` ，在 Node.js 环境中是 `global` 对象）。

02. **函数调用中的 this**：
   - 当函数作为普通函数调用时， `this` 也会指向全局对象（严格模式下为 `undefined` ）。
   - 使用 `call` , `apply` , `bind` 方法调用函数时， `this` 的值可以被明确指定。

03. **对象方法中的 this**：
   - 当函数作为对象的方法调用时， `this` 将指向调用该方法的对象。
   - 例如： `let obj = { method: function() { console.log(this); } }; obj.method();` 在这里， `this` 将指向 `obj` 。

04. **构造函数中的 this**：
   - 在使用 `new` 关键字调用构造函数时，新创建的对象会绑定给 `this` 。
   - 如： `function Person(name) { this.name = name; } let person = new Person('Tom');` 此时 `this` 指向新创建的 `person` 实例。

05. **事件处理函数中的 this**：
   - 在DOM事件处理函数中， `this` 通常指向触发事件的元素（在非严格模式下）。
   - 在addEventListener等现代方法中，如果不使用箭头函数（ `=>` ）， `this` 同样指向触发事件的元素。

06. **箭头函数中的 this**：
   - 箭头函数没有自己的 `this` ，它会捕获其所在（即定义位置）上下文的 `this` 值，无论它在哪里被调用。
   - 因此，箭头函数不能作为构造函数使用，也无法通过 `call` 、 `apply` 、 `bind` 改变 `this` 的指向。

总的来说， `this` 在 JavaScript 中的指向是动态的，取决于函数调用的方式和上下文环境。理解 `this` 的行为对于编写高质量的JavaScript代码至关重要。

### 说说new操作符具体干了什么?

`new` 操作符在 JavaScript 中用于创建一个特定类型的新对象实例。当你在 JavaScript 中使用 `new` 关键字与构造函数一起工作时，它执行以下一系列操作：

01. **创建新对象**：
   - `new` 首先会在内存中创建一个新的空对象。
  + 这个新对象会被设置为构造函数的实例，也就是说，它的内部 `[[Prototype]]`（可以通过 `__proto__` 或 `Object.getPrototypeOf()` 访问）被指向构造函数的 `prototype` 属性所指向的对象。

02. **绑定 this**：
   - 新创建的对象会被当作 `this` 关键字的上下文，当构造函数被调用时，函数体内部的 `this` 将指向这个新创建的对象。

03. **执行构造函数**：
   - 构造函数被执行，其内部的代码开始执行，初始化新对象的属性和方法。

04. **返回新对象**：
   - 构造函数如果没有返回一个非原始值（即非 `null` 、 `undefined` 、 `number` 、 `string` 、 `boolean` 和 `symbol` 类型以外的对象），那么 `new` 操作符将会返回新创建并经过构造函数初始化后的对象。
   - 如果构造函数显式返回一个对象（即一个引用类型，如数组、对象等），那么 `new` 操作符会返回构造函数返回的这个对象，而不是初始创建的对象。

综合以上步骤， `new` 操作符不仅创建了一个新的对象实例，还完成了构造函数的调用、 `this` 绑定以及原型链的设定，确保新对象能够继承构造函数原型上的属性和方法。这使得我们能够在 JavaScript 中实现基于原型的面向对象编程。

### bind、 call、apply区别? 如何实现一个bind?

`bind` 、 `call` 、 `apply` 都是 JavaScript 中用于改变函数执行上下文中 `this` 指向的方法，但它们之间存在一些关键差异：

01. **bind()**：
   - `Function.prototype.bind()` 方法创建一个新的函数，当调用新函数时，其 `this` 值会被指定为 `bind` 第一个参数提供的值，同时可以预设剩余参数供原函数调用。
   - `bind` 不会立即执行函数，而是返回一个已绑定 `this` 和预设参数的新函数。

   示例：
   

```javascript
   function MyClass() {}
   MyClass.prototype.myMethod = function(a, b) {
       console.log(this, a, b);
   };

   const boundFn = MyClass.prototype.myMethod.bind({
       customThis: 'value'
   }, 'arg1');
   boundFn('arg2'); // 输出: {customThis: 'value'} 'arg1' 'arg2'
```

02. **call()**：
   - `Function.prototype.call()` 方法调用一个函数，同时指定 `this` 的值为第一个参数，并且剩余参数直接传递给函数调用。
   - `call` 立即执行函数，并将结果返回（如果有）。

   示例：
   

```javascript
   function sum(a, b) {
       console.log(this);
       return a + b;
   }

   sum.call({
       customThis: 'value'
   }, 1, 2); // 输出: {customThis: 'value'}
   // 结果是立即计算并返回的: 3
```

03. **apply()**：
   - `Function.prototype.apply()` 方法与 `call()` 类似，也是调用一个函数，但它接收两个参数：第一个参数同样用于指定 `this` 的值，而第二个参数必须是一个数组（或类数组对象），数组中的元素将作为单独的参数传递给原函数。
   - 同样， `apply` 也是立即执行函数并可能返回结果。

   示例：
   

```javascript
   function multiply(a, b) {
       console.log(this);
       return a * b;
   }

   multiply.apply({
       customThis: 'value'
   }, [3, 4]); // 输出: {customThis: 'value'}
   // 结果是立即计算并返回的: 12
```

实现一个简易版的 `bind` 方法：

```javascript
if (!Function.prototype._myBind) {
    Function.prototype._myBind = function(context /* , ...args */ ) {
        const self = this;
        const args = Array.prototype.slice.call(arguments, 1);

        return function() {
            const innerArgs = Array.prototype.slice.call(arguments);
            return self.apply(context, [...args, ...innerArgs]);
        };
    };
}

// 使用示例：
function add(a, b) {
    console.log(this);
    return a + b;
}

const boundAdd = add._myBind({
    context: 'bound'
}, 1);
console.log(boundAdd(2)); // 输出: {context: 'bound'}，结果是：3
```

上述简易版 `bind` 方法实现并不完全等同于原生 `bind` ，因为它不支持部分应用（即预先只提供部分参数），也不支持 `new` 调用时的行为。完整实现还需要考虑更多的边界条件和兼容性问题。

### JavaScript中执行上下文和执行栈是什么?

在JavaScript中，执行上下文（Execution Contexts）和执行栈（Call Stack）是JavaScript引擎执行代码时的两个核心概念，它们共同决定了代码的执行顺序和变量访问规则。

#### 执行上下文（Execution Contexts）

执行上下文是JavaScript引擎在执行代码时创建的一个抽象概念，它代表了代码执行的环境，记录了变量、函数和对象的作用域链、变量环境以及其他相关的信息。JavaScript中有三种类型的执行上下文：

01. **全局执行上下文**：
   - 创建于JavaScript程序启动时，只有一个全局执行上下文。
   - 包含全局变量和函数声明， `this` 关键字在这个上下文中指向全局对象（在浏览器环境下是 `window` 对象）。

02. **函数执行上下文**：
   - 每次函数被调用时，都会创建一个新的函数执行上下文。
   - 包含函数内部的局部变量、参数和函数声明， `this` 关键字的指向取决于函数调用方式。

03. **Eval函数执行上下文**：
   - 由于使用 `eval` 函数动态执行代码时也会创建一个独立的作用域，但在现代JavaScript开发中通常不推荐使用 `eval` 。

#### 执行栈（Call Stack）

执行栈，也称为调用栈，是一种数据结构，采用LIFO（Last In, First Out，后进先出）的原则，用于存储正在执行的执行上下文。当JavaScript引擎开始执行脚本时，首先会将全局执行上下文压入执行栈中。此后，每调用一个函数，就会为该函数创建一个新的执行上下文，并将其压入栈顶。当函数执行完成时，相应的执行上下文就会从栈中弹出，然后控制流回到栈中上一个执行上下文。

执行栈的工作原理如下：
01. 引擎遇到函数调用时，创建新的函数执行上下文并压入栈中。
02. 引擎执行栈顶的执行上下文，处理变量赋值、函数调用、条件判断等。
03. 当函数执行完毕（或遇到`return`语句）时，该函数的执行上下文从栈中弹出。
04. 如果栈中仍有其他执行上下文，则转去执行下一个上下文，直至栈为空。

执行栈的管理和控制着代码的同步执行顺序，当栈满（例如因递归调用无终止条件导致栈溢出）或出现未捕获错误时，程序会抛出错误。了解执行上下文和执行栈对于分析和解决JavaScript中的作用域、闭包、异步调用等问题非常重要。

### 说说JavaScript中的事件模型

JavaScript 中的事件模型主要用于描述当用户或浏览器执行某个动作（如点击按钮、页面加载完成、键盘输入等）时，浏览器如何响应这些动作以及如何触发相关的 JavaScript 代码执行的过程。随着 JavaScript 标准的发展，事件模型经历了多个阶段的变化和改进，主要包括：

01. **DOM0 级事件模型**：
   - 这是最原始的事件绑定方式，通过直接在 DOM 元素上设置事件处理函数，如 `element.onclick = function() {...}` 。
   - 特点是每个事件类型只能绑定一个处理器，后续赋值会覆盖先前的绑定。
   - 解除事件绑定只需将事件处理函数设为 `null` ，如 `element.onclick = null` 。

02. **DOM2 级事件模型**：
   - 提供了标准的 `addEventListener` 和 `removeEventListener` 方法，允许为同一个事件类型添加多个处理器，并按照添加的顺序依次执行。
   - 事件对象（Event object）在事件触发时被传递给处理器，提供了更多关于事件本身的详细信息。
   - 引入了事件捕获和事件冒泡两种事件传播机制：

     - **事件捕获**：事件首先由最外层（document）向下传播至目标元素。
     - **事件冒泡**：事件首先在目标元素上触发，然后沿DOM树向上逐级传播到最外层。

   - 通过 `useCapture` 参数可以选择监听事件捕获阶段还是冒泡阶段，默认情况下事件监听器处于冒泡阶段。

03. **IE 专有的事件模型**：
   - IE 浏览器早期支持 `attachEvent` 和 `detachEvent` 方法，与 DOM2 规范略有不同。
   - 事件传播仅支持事件冒泡，没有事件捕获阶段。
   - 事件处理函数的 `this` 指针在 IE 中指向全局对象 `window` ，而在标准 DOM2 事件中， `this` 指向触发事件的元素。

04. **跨浏览器兼容性**：
   - 为了在不同的浏览器中都能正常处理事件，开发者需要写兼容性代码，比如使用 `addEventListener` 和 `attachEvent` 的组合。

现代浏览器大多都支持 DOM2 级事件模型，不过在开发过程中仍需注意旧版浏览器的兼容性问题。此外，还有一些高级特性如自定义事件（CustomEvent）、事件委托（Event Delegation）等，进一步丰富了JavaScript事件处理的能力。

### 解释下什么是事件代理? 应用场景?

事件代理（Event Delegation）是一种在JavaScript中优化事件处理的技术，它利用了事件冒泡（event bubbling）机制。事件冒泡是指当一个事件在DOM元素上触发时，该事件不仅会在触发事件的元素上触发，还会依次向上冒泡到其所有祖先元素，直到根（通常是 `document` ）。

事件代理的做法是不再为每一个子元素分别绑定事件处理器，而是将事件处理器绑定到它们的共同父元素上。当父元素接收到冒泡上来的子元素事件时，通过检查事件的目标（event.target）属性，确定事件的实际源头，然后在事件处理器内根据需要做出相应的反应。

**应用场景**：

01. 动态生成的内容：如果页面上有大量动态生成或更新的子元素（如列表项、表格行等），为每个子元素都单独绑定事件处理器会造成性能开销。通过事件代理，只需要在它们的父容器上绑定一次事件处理器即可。

02. 大量元素需要相同事件处理：例如，一个列表有很多列表项，每个列表项都需要点击事件。使用事件代理，只需在列表本身上绑定一个点击事件处理器，通过判断事件目标是哪个列表项，进而执行相应的操作。

03. 优化性能和内存占用：减少事件处理器的数量有助于提高页面性能，特别是在大型Web应用程序中，可以显著降低内存消耗和提升响应速度。

举例说明：

```javascript
// HTML结构
<
ul id = "list" >
    <
    li > Item 1 < /li> <
li > Item 2 < /li> <!--...更多列表项-- > < /
ul >

    // JavaScript 事件代理
    const list = document.getElementById("list");
list.addEventListener("click", function(event) {
    if (event.target.tagName === "LI") {
        console.log("Clicked on:", event.target.textContent);
        // 在这里可以根据 event.target 进行额外的操作
    }
});
```

在这个例子中，所有的列表项点击事件都被委托给了父元素 `<ul>` ，无需分别为每个 `<li>` 单独绑定事件处理器。当点击任何一个列表项时，事件会冒泡到 `<ul>` 上，然后在此处的处理器中进行处理。

### 说说你对闭包的理解? 闭包使用场景

JavaScript中的闭包（Closure）是一个功能强大的特性，它涉及到作用域链和变量持久化的问题。简而言之，闭包是一个函数，它可以访问并操作在其自身作用域之外的变量，这些变量通常包括函数外部作用域（父函数作用域）内的变量以及全局作用域下的变量。闭包的核心在于，当父函数执行完毕后，其作用域内的变量本应随着函数调用结束而销毁，但若父函数返回了一个内部函数，并且这个内部函数被保留下来（如赋值给一个变量或作为回调函数），那么即便父函数已经执行完毕，其作用域仍然会被内部函数所引用，形成了所谓的“闭包”。

**闭包的形成过程**：
01. 当一个函数（称为内部函数）在另一个函数（称为外部函数）内部被定义时，内部函数可以访问外部函数的所有变量和参数。
02. 当外部函数返回内部函数时，内部函数携带了对外部函数作用域的引用，即使外部函数已经执行完毕，这部分作用域没有被垃圾回收机制清除。
03. 因此，无论何时何地调用这个返回的内部函数，它都能够继续访问并操作外部函数当时存在的那些变量。

**闭包的应用场景**：

01. **数据私有化与封装**：闭包可用于实现私有变量，保护数据不被外界直接访问，只通过暴露的公共接口（通常是内部函数）来操作这些变量。

   

```javascript
   function counter() {
       let count = 0;
       return function() {
           count++;
           return count;
       };
   }

   const increaseCount = counter();
   console.log(increaseCount()); // 输出：1
   console.log(increaseCount()); // 输出：2
```

02. **异步编程**：闭包在处理回调函数时很常见，尤其是在定时器（setTimeout/setInterval）、Promise 或者 AJAX 请求中，用来保持对回调函数执行时所需变量的引用。

   

```javascript
   function delayedAlert(message, timeout) {
       setTimeout(function() {
           alert(message); // 即使在timeout之后，message仍能被正确获取
       }, timeout);
   }

   delayedAlert('Hello, World!', 2000);
```

03. **模块化**：闭包可以模拟私有作用域，用于构建模块系统，确保模块内的变量不会污染全局空间。

04. **事件监听器**：在DOM编程中，常常利用闭包来绑定事件处理器，使得处理器可以访问定义时的状态。

   

```javascript
   function attachClickHandler(elementId) {
       let element = document.getElementById(elementId);
       element.addEventListener('click', function() {
           console.log('Clicked:', this.id); // 此处能访问elementId
       });
   }

   attachClickHandler('myButton');
```

总结来说，闭包在JavaScript中扮演着关键角色，它帮助开发者实现变量隐藏、状态保持、异步控制等多种高级功能，是实现很多复杂逻辑的基础构造单元。然而，由于闭包可能导致内存泄漏（如果闭包持续引用不再使用的资源），所以在实际开发中也需要合理管理和释放闭包所持有的资源。

### 谈谈JavaScript中的类型转换机制

JavaScript中的类型转换机制主要是指在某些操作或函数调用中，JavaScript引擎会自动或手动将一种数据类型转换为另一种数据类型的过程。JavaScript是一种动态类型语言，它允许不同类型的数据之间的相互转换，主要有以下几种类型转换：

01. **显式类型转换**：
   - **Number()**: 将变量转换为数字类型，例如 `Number('123')` 返回 `123` ， `Number('abc')` 返回 `NaN` 。
   - **String()**: 将变量转换为字符串类型，例如 `String(123)` 返回 `"123"` 。
   - **Boolean()**: 将变量转换为布尔类型，例如 `Boolean(0)` 返回 `false` ， `Boolean('')` 返回 `false` 。
   - **parseInt() 和 parseFloat()**: 分别将字符串转换为整数或浮点数，忽略非数字字符开头的部分。
   - **toString()**: 对象或基本类型调用该方法可以转换为字符串。

02. **隐式类型转换**：
   - **算术运算符**: 在进行数学运算时，非数字类型会自动转换为数字，例如 `'2' + 2` 返回 `"22"` ， `'2' - 2` 返回 `0` 。
   - **比较运算符**: 在进行比较时，不同类型之间会进行类型转换以便进行比较，例如 `'' == 0` 返回 `true` 。
   - **逻辑运算符**: 在逻辑表达式中，非布尔值会被转换为布尔值参与逻辑运算，例如 `!''` 返回 `true` ，因为空字符串转换为布尔值为 `false` 。
   - **条件运算符**: `if` 、 `?:` 等条件语句中也会发生隐式转换。

03. **ToPrimitive** 抽象操作：
   - 在JavaScript内部，当需要将对象转换为其基本值形式时，会调用 `ToPrimitive(input, hint)` 抽象操作。 `hint` 可以是 `Number` 或 `String` ，表明期望的原始类型。转换过程会首先尝试调用对象的 `valueOf()` 方法，如果没有得到原始值，则尝试调用 `toString()` 方法。

04. **特殊转换情况**：
   - `null` 和 `undefined` 在转换为数字时都是 `NaN` ，转换为字符串时分别是 `"null"` 和 `"undefined"` 。
   - `null` 、 `undefined` 、 `NaN` 、空字符串 ( `''` )、零 ( `0` ) 和空对象 ( `{} or new Object()` 在转换为布尔值时均为 `false` ，其余值为 `true` 。

类型转换机制在JavaScript中广泛应用，但也可能导致一些不易察觉的错误，特别是涉及隐式类型转换时，因此建议尽量避免不必要的类型转换，并在编程时保持类型清晰和一致。

### 深拷贝浅拷贝的区别? 如何实现一个深拷贝?

深拷贝和浅拷贝是针对对象（包括数组、对象等引用类型）复制时的两种不同策略。

**浅拷贝（Shallow Copy）**：
* 当执行浅拷贝时，仅仅复制了对象的第一层属性值，如果属性值是基本类型（如数字、字符串、布尔值等），则直接复制其值；但如果属性值是对象（包括数组、函数或其他引用类型），则复制的是这个引用类型的引用地址，而不是其实际内容。
* 结果是新旧对象指向的是同一个引用类型的实例，更改其中一个对象的嵌套对象属性时，会影响到另一个对象。

**深拷贝（Deep Copy）**：
* 深拷贝则是递归地复制整个对象及其所有层级的属性，即使属性值是对象，也会创建这个对象的一个全新副本，而不是复制引用。
* 通过深拷贝得到的新对象与原对象完全独立，修改其中一个对象的属性不会影响到另一个对象。

**如何实现一个深拷贝：**

在JavaScript中，实现深拷贝有许多种方法，下面是一些常见的实现方式：

01. **JSON.parse 和 JSON.stringify**：
   - 这种方法简洁易用，但有局限性，不适用于包含函数、循环引用的对象、Symbol类型属性、不可序列化的对象（如Date、RegExp、Map、Set等）。

   

```javascript
   function deepCopy(obj) {
       return JSON.parse(JSON.stringify(obj));
   }
```

02. **递归复制**：
   - 通过递归遍历对象或数组的所有属性，如果是基本类型就直接复制，如果是对象或数组则再次调用深拷贝函数。

   

```javascript
   function deepCopy(obj, hash = new WeakMap()) {
       if (obj instanceof RegExp) return new RegExp(obj);
       if (obj instanceof Date) return new Date(obj);
       if (obj instanceof Set) return new Set(Array.from(obj).map(item => deepCopy(item)));
       if (obj instanceof Map) return new Map(Array.from(obj.entries()).map(([key, val]) => [deepCopy(key), deepCopy(val)]));
       if (obj === null || typeof obj !== 'object') return obj;
       if (hash.has(obj)) return hash.get(obj);

       let cloneObj = new obj.constructor();
       hash.set(obj, cloneObj);

       for (let key in obj) {
           if (obj.hasOwnProperty(key)) {
               cloneObj[key] = deepCopy(obj[key], hash);
           }
       }
       return cloneObj;
   }
```

03. **lodash库的_.cloneDeep**：
   - 使用第三方库如lodash，提供了现成的深拷贝函数，它可以处理大部分复杂的深拷贝需求。

   

```javascript
   import _ from 'lodash';
   let newObj = _.cloneDeep(originalObj);
```

请注意，由于JavaScript的复杂性，自己实现深拷贝函数可能会面临许多边缘情况，使用成熟的库或者框架提供的深拷贝工具往往是更为可靠的选择。对于非常复杂的对象结构，尤其是包含循环引用的情况，自定义实现时需要特别小心处理，以防止死循环。

### Javascript中如何实现函数缓存? 函数缓存有哪些应用场景?

在JavaScript中实现函数缓存通常是为了避免对于相同的输入参数多次执行耗时的计算，通过将函数的输出结果保存起来，当下次同样的参数传入时，可以直接返回之前缓存的结果，从而提高程序性能。实现函数缓存的一种常见方法是利用闭包和一个对象（如Map或对象字面量）来存储结果。以下是一个简单的使用对象作为缓存容器的函数缓存实现：

```javascript
function memoize(func) {
    const cache = {};

    return function(...args) {
        const key = JSON.stringify(args); // 将参数转化为字符串作为缓存的键
        if (cache.hasOwnProperty(key)) {
            return cache[key];
        } else {
            const result = func.apply(this, args);
            cache[key] = result;
            return result;
        }
    };
}

// 假设有一个高代价的计算函数
function expensiveCalculation(a, b) {
    // 这里模拟耗时计算
    // 实际应用中可能是复杂的计算、网络请求等
    console.log('Performing calculation...');
    return a * b;
}

// 为昂贵计算函数加上缓存功能
const cachedExpensiveCalculation = memoize(expensiveCalculation);

// 第一次调用，执行实际计算
let result1 = cachedExpensiveCalculation(2, 3);
// 第二次调用，直接返回缓存结果
let result2 = cachedExpensiveCalculation(2, 3);

console.log(result1); // 输出：6（执行计算）
console.log(result2); // 输出：6（从缓存中读取，不执行计算）
```

函数缓存的应用场景：

01. **频繁计算的函数**：对于那些计算成本较高，但输入相对固定或重复的函数，如斐波那契数列、阶乘、大整数乘法等。

02. **递归函数优化**：递归函数中可能会遇到相同的子问题，通过缓存可以避免重复计算，比如动态规划问题的解决方案。

03. **数据接口请求**：在网络请求中，对于同一份数据的重复请求，可以通过缓存请求结果来减少服务器压力，加快客户端响应速度。

04. **数据转换处理**：在数据处理流程中，如果存在对同一份数据做多次相同转换操作的情况，通过函数缓存可以避免不必要的重复转换。

05. **React/Vue等前端框架中渲染优化**：在虚拟DOM diff算法中，可以使用函数缓存来优化计算节点差异的过程，减少重复计算的成本。

### 说说你对事件循环的理解

事件循环（Event Loop）是JavaScript运行时环境（如浏览器或Node.js）中负责协调异步任务执行的核心机制。JavaScript引擎（如V8）通过事件循环来管理同步代码执行、微任务队列、宏任务队列以及IO和UI线程之间的交互。

事件循环大致工作流程如下：

01. **执行全局脚本**：
   - 当JavaScript引擎开始执行一段全局脚本时，它首先执行所有的同步代码。
   - 同步代码按顺序逐行执行，期间如果遇到异步操作（如setTimeout、Promise、I/O、事件监听器等），它们并不会阻塞主线程的执行，而是被挂起并安排到适当的队列中等待执行。

02. **任务队列**：
   - JavaScript的任务队列分为宏任务（Macro Task）队列和微任务（Micro Task）队列。
   - 宏任务包括： `setTimeout` 、 `setInterval` 、 `setImmediate` （Node.js环境）、I/O、UI渲染等。
   - 微任务包括： `Promise.then` 、 `MutationObserver` 、 `process.nextTick` （Node.js环境）等。

03. **执行过程**：
   - 当所有同步代码执行完毕后，事件循环首先检查并执行所有待处理的微任务。
   - 微任务队列一旦执行完，事件循环便开始处理宏任务队列的第一个任务。
   - 当宏任务执行完毕，事件循环会再次查看是否有待处理的微任务，若有，则执行所有微任务，然后再次处理下一个宏任务。
   - 这样的过程会一直持续下去，形成一个循环，直到没有任何待处理的任务。

04. **渲染/UI更新**：
   - 在浏览器环境中，每一轮事件循环结束后，浏览器会检查是否需要重新渲染页面（如果在这轮循环中有过页面变更）。

简单来说，事件循环确保了JavaScript引擎能够有序地执行同步和异步任务，平衡了任务执行和页面渲染的关系，使得JavaScript既能处理异步I/O，又能及时响应用户的交互操作。正是由于事件循环的存在，JavaScript才能实现非阻塞式的异步编程模型。

### JavaScript字符串的常用方法有哪些?

JavaScript中字符串的常用方法非常多，这里列举一部分主要的方法：

01. **连接字符串**：
   - `+` 运算符：可以用于字符串拼接。
   - `String.prototype.concat()` ：连接一个或多个字符串并返回新的字符串。

02. **获取字符串信息**：
   - `length` 属性：返回字符串的长度。
   - `charAt(index)` ：返回指定索引位置的字符。
   - `charCodeAt(index)` ：返回指定索引位置字符的Unicode编码。
   - `codePointAt(index)` ：返回指定索引位置字符的UTF-16编码单元的 Unicode 编码点（ES6新增）。
   - `startsWith(searchString[, position])` ：检查字符串是否以指定的子字符串开头。
   - `endsWith(searchString[, endPosition])` ：检查字符串是否以指定的子字符串结尾。
   - `includes(searchString[, position])` ：检查字符串是否包含指定的子字符串。

03. **查找和替换**：
   - `indexOf(searchValue[, fromIndex])` ：返回指定子字符串在原字符串中首次出现的索引，未找到则返回-1。
   - `lastIndexOf(searchValue[, fromIndex])` ：返回指定子字符串在原字符串中最后一次出现的索引，未找到则返回-1。
   - `search(regexp)` ：使用正则表达式查找字符串，返回匹配项的索引，未找到则返回-1。
   - `match(regexp)` ：使用正则表达式查找字符串并返回匹配项，如果无匹配则返回 `null` ，否则返回匹配数组。
   - `replace(regexp|substr, newSubstr|function)` ：替换匹配项，可以用新的子字符串替换匹配到的内容，也可以用函数动态生成新的子字符串。

04. **截取和分割字符串**：
   - `substring(indexStart[, indexEnd])` ：返回从 `indexStart` 开始到 `indexEnd` （不包括）之间的子字符串。
   - `substr(start[, length])` ：从指定位置开始截取指定长度的子字符串。
   - `slice(start[, end])` ：返回从 `start` 开始到 `end` （不包括）之间的子字符串，支持负数索引。
   - `split([separator[, limit]])` ：根据指定的分隔符将字符串分割为数组。

05. **大小写转换**：
   - `toLowerCase()` ：将字符串转换为全小写。
   - `toUpperCase()` ：将字符串转换为全大写。

06. **字符串填充**（ES6新增）：
   - `padStart(targetLength[, padString])` ：在字符串头部填充指定字符，达到目标长度。
   - `padEnd(targetLength[, padString])` ：在字符串尾部填充指定字符，达到目标长度。

07. **模板字符串（ES6新增）**：
   - ` `  ` ${expression} `  ` ` ：用于字符串插值，可以嵌入表达式和变量值。

08. **其他实用方法**：
   - `trim()` ：移除字符串两侧的空白字符。
   - `trimLeft()` / `trimStart()` ：移除字符串左侧的空白字符（ES2019）。
   - `trimRight()` / `trimEnd()` ：移除字符串右侧的空白字符（ES2019）。

以上只是JavaScript字符串方法的一部分，还有其他如编码解码相关的 `encodeURI()` , `encodeURIComponent()` , `decodeURI()` , `decodeURIComponent()` 等方法。

### 数组的常用方法有哪些?

JavaScript数组的常用方法非常丰富，以下是一些关键的数组操作方法：

01. **添加/插入元素**：
   - `push(item1, ..., itemN)` ：在数组末尾添加一个或多个元素，并返回新的数组长度。
   - `unshift(item1, ..., itemN)` ：在数组开头添加一个或多个元素，并返回新的数组长度。

02. **删除/移除元素**：
   - `pop()` ：移除数组的最后一个元素，并返回该元素的值。
   - `shift()` ：移除数组的第一个元素，并返回该元素的值。
   - `splice(start, deleteCount, item1, ..., itemX)` ：从数组中删除指定数量的元素，并可选择性地向数组中添加新元素。返回被删除的元素数组。

03. **合并数组**：
   - `concat(array1, array2, ..., itemN)` ：创建并返回一个新的数组，它是通过连接两个或更多数组及/或值组成的一个数组。

04. **访问与切片**：
   - `slice(start[, end])` ：提取数组的一部分，并返回一个新的数组，不改变原数组。
   - `join(separator)` ：将数组的所有元素转化为字符串形式，然后用指定的分隔符连接起来，返回一个字符串。

05. **排序**：
   - `sort(compareFunction)` ：对数组的元素进行排序，默认按字典顺序排列，可以通过自定义比较函数来实现特定排序规则。

06. **反转数组**：
   - `reverse()` ：颠倒数组中元素的顺序。

07. **迭代与遍历**：
   - `forEach(callback(currentValue, index, array), thisArg)` ：对数组的每个元素执行提供的函数，没有返回值。
   - `map(callback(currentValue, index, array), thisArg)` ：创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。
   - `filter(callback(element, index, array), thisArg)` ：创建一个新数组，其包含通过所提供函数实现的测试的所有元素。
   - `reduce(callback(accumulator, currentValue, currentIndex, array), initialValue)` ：对数组中的每个元素执行一个由您提供的reducer函数(升序执行)，将其结果汇总为单个返回值。

08. **查找元素**：
   - `indexOf(searchElement[, fromIndex])` ：返回指定元素在数组中第一次出现的位置，未找到时返回-1。
   - `lastIndexOf(searchElement[, fromIndex])` ：返回指定元素在数组中最后一次出现的位置，未找到时返回-1。
   - `includes(searchElement[, fromIndex])` ：判断数组是否包含某个指定的值，返回布尔值。

09. **其他方法**：
   - `entries()` , `keys()` , `values()` （ES6）：返回迭代器，分别用于遍历数组的键值对、键名和键值。
   - `find(callback(element, index, array), thisArg)` ：查找数组中第一个满足提供的测试函数的元素，否则返回 `undefined` 。
   - `findIndex(callback(element, index, array), thisArg)` ：返回数组中满足提供的测试函数的第一个元素的索引，否则返回-1。
   
以上列出的是JavaScript数组部分核心且常用的方法，实际应用中还有很多其他的方法和技巧，比如 `flatMap()` 、 `copyWithin()` 等（取决于JavaScript版本）。

### Javascript本地存储的方式有哪些? 区别及应用场景?

JavaScript在浏览器环境中提供了多种本地存储的方式来持久化数据，主要包括：

01. **localStorage**：
   - **特点**：永久存储在用户浏览器中，直到被明确删除或浏览器清理本地存储空间。不受页面刷新或关闭的影响，容量限制大约为5MB。
   - **应用场景**：适合存储长久不变的用户配置信息、访问历史、主题设置等不需要保密且需要长期存在的数据。

02. **sessionStorage**：
   - **特点**：数据仅在当前会话（浏览器窗口或标签页）有效，当窗口关闭时数据将被清除。同样大约有5MB的存储限制。
   - **应用场景**：用于临时存储用户在当前浏览会话中的状态信息，如购物车商品、临时表单数据等，当用户离开网站或关闭窗口时，这些数据无需保留。

03. **Cookies**：
   - **特点**：由服务器发送到浏览器的小型文本文件，每次HTTP请求都会携带回服务器。容量较小，一般限制在4KB左右，且可能影响性能和隐私设置。
   - **应用场景**：常用于认证、个性化设置、跟踪用户状态等，虽然也能存储少量数据，但由于其与HTTP请求密切相关，所以不适合存储大量的本地数据。

04. **IndexedDB**：
   - **特点**：一个NoSQL数据库系统，支持键值对和结构化数据的存储，理论上存储空间远大于localStorage，且支持事务操作和高效查询。
   - **应用场景**：适合存储大量结构化数据，如离线应用、游戏进度、媒体文件元数据等。

05. **Web Storage API扩展**：
   - **Cache API**：专门用于缓存资源，如HTML文档、图片等。
   - **Service Workers Cache**：配合Service Worker，用于实现离线应用和服务端推送更新等高级功能。
   - **File System API**（受限于浏览器安全政策，现已废弃）：曾经允许网页直接访问用户磁盘空间进行文件读写操作。

对比：

* **localStorage** 和 **sessionStorage** 主要用于存储键值对数据，易于操作，但不适合存储大量结构化数据或文件。
* **Cookies** 用于跨页面和跨请求间传递状态信息，受HTTP协议约束，较早的存储方案，现在逐渐被Web Storage替代。
* **IndexedDB** 提供了更加强大的数据存储能力，适合处理更大规模的数据和更复杂的查询需求。
* **Cache API** 和 **Service Workers Cache** 主要服务于离线应用和资源优化，而不一定作为通用的数据存储方案。

根据数据的需求（持久性、安全性、大小、是否需要随请求发送等），开发者可以选择合适的方式来存储JavaScript中的本地数据。

### 大文件上传如何做断点续传?

大文件上传的断点续传是在网络不稳定或者用户主动暂停上传后，能够在重新上传时从上次失败或暂停的地方继续上传的功能。以下是实现大文件断点续传的基本步骤和技术要点：

01. **分块上传**
   - 将大文件分割成多个小块，每个小块独立上传。
   - 每个小块都可以有自己的唯一标识，通常包括文件ID和块的序号。

02. **记录上传进度**
   - 保存每个文件块上传成功与否的状态，可以存储在服务器端或者客户端的本地存储（如localStorage或IndexedDB）中。
   - 记录每个块的大小以及上传的起始位置（偏移量）。

03. **检测已上传部分**
   - 当重新开始上传时，客户端首先从服务器或本地存储中获取已上传文件块的状态。
   - 根据这些状态信息，确定需要继续上传的文件块范围。

04. **发起续传请求**
   - 对于尚未上传成功的文件块，客户端从上次失败的地方开始读取文件内容，然后发送续传请求。
   - 请求中需要包含文件块的标识以及该块的开始位置和数据。

05. **服务器端处理**
   - 服务器端接收到续传请求后，检查请求中包含的块信息是否合法。
   - 若合法，则在服务器端对应的临时文件中定位到对应位置，接着写入新的数据块。

06. **完整性校验**
   - 在所有文件块上传完成后，客户端可能需要发送一个完整性校验请求，通过MD5、SHA-1等哈希算法校验服务器端文件与客户端原始文件的一致性。
   - 服务器端在收到所有分块并完成拼接后，也进行同样的校验，确保文件完整无误。

07. **合并文件**
   - 当所有分块上传并校验无误后，服务器端将所有分块合并成完整的文件，并更新文件状态为已完成。

以下是一个简化版的伪代码示例：

```javascript
// 客户端
function uploadLargeFile(file, chunkSize) {
    const chunks = splitFileIntoChunks(file, chunkSize);
    const uploadedChunks = loadUploadedChunkStatuses();

    for (let i = 0; i < chunks.length; i++) {
        if (!uploadedChunks[i]) {
            const start = i * chunkSize;
            const blobSlice = File.prototype.slice || File.prototype.mozSlice || File.prototype.webkitSlice;
            const chunk = blobSlice.call(file, start, start + chunkSize);

            uploadChunk(chunk, file.id, i); // 发送分块上传请求
        }
    }
}

function uploadChunk(chunk, fileId, chunkIndex) {
    // 发送POST请求，包含chunk数据和chunk的索引信息
    fetch('/upload', {
            method: 'POST',
            body: chunk,
            headers: {
                'Content-Type': 'application/octet-stream',
                'File-ID': fileId,
                'Chunk-Index': chunkIndex,
            },
        })
        .then(response => handleUploadResponse(response, fileId, chunkIndex));
}

// 服务器端
app.post('/upload', (req, res) => {
    const fileId = req.headers['file-id'];
    const chunkIndex = req.headers['chunk-index'];
    const chunkData = req.body;

    // 写入临时文件相应位置
    writeChunkToFile(fileId, chunkIndex, chunkData);

    // 更新上传状态
    updateChunkUploadStatus(fileId, chunkIndex, true);

    res.status(200).send('Chunk uploaded successfully');
});

// 文件上传完成后，进行完整性校验并合并文件
// ...
```

请根据实际情况调整代码以适应具体的开发环境和框架，如使用axios、fetch或者其他HTTP客户端库，以及相应的服务器端API设计。同时，为了应对并发上传和失败重试等问题，还需加入额外的错误处理和并发控制逻辑。

### ajax原理是什么? 如何实现?

Ajax（Asynchronous JavaScript and XML）是一种让网页能在不重新加载整个页面的情况下与服务器交换数据并更新部分网页的技术。尽管名字包含了XML，但实际开发中，数据格式更多的是JSON而非XML。

**Ajax原理**：
Ajax的工作原理依赖于浏览器提供的XMLHttpRequest对象或Fetch API，以及其他辅助手段（如JSON-P、CORS等）。

01. **异步请求**：
   XMLHttpRequest对象或Fetch API允许JavaScript创建一个新的HTTP请求，这个请求与主页面的加载无关，是异步发生的。

02. **服务器通信**：
   JavaScript脚本创建并初始化XMLHttpRequest对象，设置请求类型（GET、POST等）、URL及其他参数，然后发送请求到服务器。

03. **数据交换**：
   服务器接收到请求后，处理请求并返回数据，这个数据可以是任何格式，如XML、JSON、HTML片段等。

04. **回调处理**：
   当服务器响应返回时，XMLHttpRequest对象的readyState属性发生变化，触发onreadystatechange事件。此时，可以通过检查xhr.readyState和xhr.status来确认请求是否成功完成，然后通过xhr.responseText获取服务器返回的数据。

05. **DOM操作**：
   获得服务器返回的数据后，JavaScript脚本可以在客户端进行处理，例如解析JSON数据或操作DOM，更新网页的部分内容。

**实现Ajax请求的简单示例**（使用XMLHttpRequest）：

```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'http://example.com/api/data', true);

xhr.onload = function() {
    if (xhr.status === 200) {
        // 请求成功
        var data = JSON.parse(xhr.responseText);
        // 更新页面内容或进行其他操作
    } else {
        // 请求失败
        console.error(xhr.statusText);
    }
};

xhr.onerror = function() {
    console.error('There was an error!');
};

xhr.send(null);
```

使用Fetch API的示例：

```javascript
fetch('http://example.com/api/data')
    .then(response => {
        if (response.ok) {
            return response.json();
        } else {
            throw new Error('Network response was not ok.');
        }
    })
    .then(data => {
        // 处理数据并更新页面
    })
    .catch(error => {
        console.error('There was an error fetching the data:', error);
    });
```

需要注意的是，以上示例仅为基本的GET请求，实际使用中还需要处理各种情况，如设置请求头、POST数据、处理错误、超时等。另外，现代JavaScript中还有jQuery、axios等库提供了更便捷的Ajax请求API。

### 说说JavaScript的垃圾回收机制

JavaScript的垃圾回收机制是一种自动内存管理方式，它的主要目的是自动回收不再使用的内存，以防止内存泄漏。JavaScript运行时环境（如浏览器的JavaScript引擎或Node.js）会跟踪对象的引用状态，当一个对象不再有任何引用指向它时，这个对象就会被认为是不可达的，垃圾回收器会在合适的时机回收这部分内存。

以下是垃圾回收机制的主要工作原理：

01. **引用计数法（Reference Counting）**：
   - 这种方法较为简单，每当有一个地方引用一个对象时，该对象的引用计数加1；当引用失效时，计数减1。当一个对象的引用计数变为0时，说明它不再被任何变量引用，可以被回收。
   - 然而，现代JavaScript引擎（如V8）并不主要依赖引用计数法，因为这种方法无法处理循环引用的情况，会导致内存泄漏。

02. **标记清除（Mark-and-Sweep）**：
   - 这是大多数现代JavaScript引擎采用的主要垃圾回收算法。垃圾回收器会定期执行一系列步骤：

     - 标记阶段：遍历所有活动对象（从全局对象开始，沿着对象图一路追踪），将所有活动对象标记为“存活”。
     - 清除阶段：遍历堆内存中的所有对象，销毁未被标记为“存活”的对象，并释放其所占用的内存。

03. **标记压缩（Mark-Compact）**：
   - 类似于标记清除，但在这个过程中，垃圾回收器还会对存活的对象进行整理，消除内存碎片。它会把存活的对象移到一起，然后释放其余的空间，从而使得堆内存中的空间更加紧凑。

04. **增量标记（Incremental Marking）**：
   - V8引擎采用了增量标记的策略，将垃圾回收的工作分散到多个周期中，避免一次性耗用大量CPU时间，降低对程序运行的影响。

05. **新生代和老生代（Young Generation and Old Generation）**：
   - 许多垃圾回收器将堆内存划分为不同的区域，如新生代和老生代。新生代存放生命周期较短的临时对象，采用复制算法；老生代存放生命周期较长的对象，采用标记清除或标记压缩算法。

总的来说，JavaScript的垃圾回收机制通过自动检测和回收不再使用的内存，极大地减轻了开发者的内存管理负担，但也要求开发者理解并避免造成不必要的内存泄漏，例如解除不再需要的对象引用等。
