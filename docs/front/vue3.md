## Vue3面试题

### Vue3.0所采用的Composition Api 与Vue2.x使用的Options Api有什么不同?

Vue3.0 引入的 Composition API 与 Vue 2.x 使用的 Options API 主要存在以下几个方面的不同：

01. **逻辑组织**：
   - **Options API**：在 Vue 2 中，组件的逻辑是基于一系列独立的选项（如 `data` 、 `methods` 、 `computed` 、 `watch` 等）来组织的。这意味着相关的数据和方法分布在不同的属性中，随着组件复杂度提升，这些分散的逻辑可能导致组件难以理解和维护。
   - **Composition API**：Vue 3 的 Composition API 提倡将组件的逻辑按照功能进行组织，开发者可以在一个单一的 `setup()` 函数中集中管理所有相关逻辑，包括状态变量（使用 `ref` 、 `reactive` 等）、计算属性（使用 `computed` 函数）、监听器（使用 `watch` 函数）等，这样有助于提高代码的可读性和复用性。

02. **作用域和封装**：
   - **Options API**：每个选项的作用域都是绑定到组件实例上的，通过 `this` 关键字访问，但这种方式有时会导致作用域混乱。
   - **Composition API**：移除了对 `this` 的依赖，通过函数和返回的对象显式地控制作用域。它允许直接导入外部函数或工具，并且更容易提取和复用逻辑。

03. **响应式系统改进**：
   - **Vue 2**：Vue 2 使用 `Object.defineProperty()` 实现对象属性的响应式，而对于数组则重写了部分原型方法以追踪变化。
   - **Vue 3**：Vue 3 的 Composition API 使用了一个全新的响应式系统，提供了 `reactive` 和 `ref` 等用于创建响应式状态的函数，以及 `toRefs` 用于解构响应式对象。

04. **代码结构灵活性**：
   - **Options API**：固定的结构使得某些场景下的代码不够灵活，例如无法轻松地在多个组件间共享逻辑。
   - **Composition API**：允许更自由地组织代码，使逻辑易于拆分和组装，更适合大型应用和团队协作，有利于代码复用和单元测试。

总结来说，Vue3 的 Composition API 更倾向于面向逻辑编程，增强了代码的组织能力和可维护性，同时保持了对 Vue2.x 选项式 API 的兼容性，开发者可以根据项目需求选择适合的编程风格。

### vue3.0的设计目标是什么? 做了哪些优化

Vue3.0 的设计目标主要包括但不限于以下几个方面：

01. **性能优化**：
   - 减少运行时体积：Vue 3.0 通过改进内部实现和利用现代 JavaScript 特性如 Proxy 替换 Object.defineProperty，使得核心库体积更小，提高了加载速度。
   - 提升运行时性能：通过优化虚拟 DOM 渲染算法和其他底层机制，Vue 3.0 比 Vue 2.x 性能提升约 1.2 到 2 倍。
   - 事件缓存 ( `cacheHandlers` )：Vue 3.0 优化了事件处理函数的创建和绑定过程，对于可缓存的事件处理函数不再重复生成，从而减少不必要的内存分配和执行开销。

02. **API 设计一致性与可维护性**：
   - 引入 Composition API：Vue 3.0 推出了 Composition API，提供一种更加灵活和集中式的逻辑组织方式，相比 Vue 2.x 的 Options API，它允许开发者更好地组织组件内部的状态和行为，方便代码复用和测试。
   - 改进了类型推断和 TypeScript 支持：Vue 3.0 对 TypeScript 的支持更为深入，提供了更完善的类型声明文件，便于大型项目的开发和维护。

03. **底层开放与扩展性**：
   - 自定义渲染 API：Vue 3.0 暴露了更多的底层接口，允许开发者根据需要自定义渲染器，例如 SSR（服务器端渲染）、WebGL 渲染或其他非DOM环境下的渲染。

04. **模块化与 tree-shaking**：
   - Vue 3.0 支持 tree-shaking，允许在构建过程中仅打包实际使用的功能模块，进一步减小生产环境下的最终代码体积。

综上所述，Vue 3.0 的设计目标在于提高整体框架的性能、代码组织的合理性、类型系统的增强以及底层架构的扩展能力，从而满足现代前端开发日益增长的需求和挑战。

### 用Vue3.0写过组件吗? 如果想实现一个Modal你会怎么设计?

在 Vue3 中，我们可以结合Composition API 和模板来创建这个组件。下面是一个简化的示例设计思路：

```html
<!-- Modal.vue -->
<template>
    <teleport to="body">
        <div v-if="visible" class="modal-container" @click.self="handleOuterClick">
            <div class="modal">
                <div class="modal-header">
                    <h3>{{ title }}</h3>
                    <button type="button" @click="close">关闭</button>
                </div>
                <div class="modal-body">
                    <slot></slot> <!-- 这里用于放置模态框主体内容 -->
                </div>
                <div v-if="hasFooter" class="modal-footer">
                    <slot name="footer"></slot> <!-- 这里用于放置模态框底部操作栏 -->
                </div>
            </div>
        </div>
    </teleport>
</template>

<script setup lang="ts">
    import {
        ref,
        onBeforeUnmount,
        onMounted
    } from 'vue';

    interface Props {
        title: string;
        hasFooter ? : boolean; // 可选属性，是否显示底部栏
    }

    const props = defineProps < Props > ();

    // 状态管理
    const visible = ref(false);

    // 显示/隐藏 modal
    function open() {
        visible.value = true;
    }

    function close() {
        visible.value = false;
    }

    // 监听外部点击以关闭模态框
    let clickOutsideHandler: EventListener;
    onMounted(() => {
        clickOutsideHandler = (e: MouseEvent) => {
            if (!e.target.closest('.modal')) {
                close();
            }
        };
        document.body.addEventListener('click', clickOutsideHandler);
    });

    onBeforeUnmount(() => {
        document.body.removeEventListener('click', clickOutsideHandler);
    });
</script>

<style scoped>
    .modal-container {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .modal {
        background-color: #fff;
        border-radius: 4px;
        padding: 20px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        max-width: 90%;
        width: 600px;
        overflow-y: auto;
    }

    /* ... 更多样式... */
</style>
```

上述组件的主要特点包括：

* 使用 `ref` 存储 Modal 是否可见的状态。
* 通过 `teleport` 元素将 Modal 容器移动到文档 body 的末尾，避免遮罩层和原页面元素层级问题。
* 在模态框外点击时触发关闭事件，确保非模态内容区域不会影响 Modal 的显示状态。
* 通过 Props 接收标题和是否有底部栏的配置。
* 使用 slots 分别注入 Modal 主体内容和底部操作栏。

要使用此 Modal 组件，在父组件中可以这样引用：

```html
<Modal title="确认删除" :hasFooter="true">
    <p>您确定要删除这条记录吗?</p>
    <template #footer>
        <button @click="handleCancel">取消</button>
        <button @click="handleConfirm">确定</button>
    </template>
</Modal>
```

然后在父组件的 methods 中定义对应的 `handleCancel` 和 `handleConfirm` 方法。

### vue3.0性能提升主要是通过哪几方面体现的?

Vue3.0 性能提升主要体现在以下几个方面：

01. **编译阶段优化**
   - **静态节点提升**（Hoisting）：Vue3 中能够识别并提升静态（不变）内容，在初次渲染后将其存储起来，后续更新时无需再次渲染这些静态内容，显著减少了不必要的DOM操作。
   - **Fragments 和 Patch Flags**：Vue3 支持 Fragment（片段），允许模板包含多个根节点，这减少了额外的DOM包裹元素；同时增加了Patch Flags来标记VNode的不同特性，使得Diff算法更加精确高效。

02. **响应式系统改进**
   - **Proxy替换defineProperty**：Vue2.x使用 `Object.defineProperty` 实现数据响应式，Vue3改用ES6的Proxy，可以更高效地监控对象的所有属性，而且Proxy可以更好地处理数组的变化，不需要像Vue2那样重写数组方法。

03. **源码体积减小**
   - **Tree Shaking**：Vue3通过重构代码，配合Rollup等现代打包工具实现了更好的Tree Shaking效果，剔除未使用的代码，有效降低生产环境下的包体积。

04. **运行时优化**
   - **事件缓存**：Vue3对静态事件处理器进行了优化，将其缓存起来，避免重复创建。
   - **Diff算法优化**：改进了虚拟DOM diff算法，针对静态节点和动态节点的区别对待，减少了不必要的对比操作。

05. **Composition API与逻辑复用**
   - **Composition API**：引入新的API组织形式，使得逻辑更加模块化，更利于代码复用和性能优化，尤其是在大型项目中可以更好地管理和分割组件间的共享状态和逻辑。

06. **组件初始化性能提升**
   - Vue3中Watcher、Effect等核心组件的优化，使得组件初始化时的性能得到提升，尤其是大量组件同时渲染时，资源利用率更高。

综合以上几点，Vue3在多个层面进行了深入的优化，从而带来了整体性能的显著提升。

###　Vue3.0里为什么要用Proxy API替代defineProperty APl?
Vue3.0 选择使用 Proxy API 替代 Object.defineProperty API 主要基于以下原因：

01. **更全面的拦截能力**：
   - `Proxy` API 提供了一种代理机制，它可以透明地代理任何类型的对象（包括数组和普通对象），并支持多达13种拦截操作，比如 `get` 、 `set` 、 `deleteProperty` 、 `ownKeys` 、 `apply` 等。相比之下， `Object.defineProperty` 只能逐个属性地设置 getter 和 setter，无法一次性代理整个对象的行为。

02. **深度监听与效率提升**：
   - 在 Vue 2.x 中，为了实现深度监听，需要递归遍历对象的所有属性来设置 getter 和 setter，当对象内部结构发生变化时（如添加新属性），原有的实现方式无法自动监测到这些变化。而 `Proxy` 可以自动捕获到对象及其后代属性的新增、修改和删除操作，无需预先知道对象的具体属性名，大大简化了响应式系统的实现。

03. **更好的性能表现**：
   - `Proxy` 的实现相对于 `defineProperty` 更加高效，特别是在频繁变动的数据结构下，由于其具有完整的代理机制，所以在对象的变更检测上能够更快速、准确地跟踪变化。

04. **便利的 API 使用体验**：
   - 使用 `Proxy` 可以统一处理对象属性的各种操作，简化了 API 的使用，并且让 Vue3 可以更优雅地处理数组的变异方法（如 push、pop、shift、unshift 等），无需像 Vue 2.x 那样重写数组原型方法。

05. **未来发展方向**：
   - `Proxy` 是 ES6 中的一个标准特性，具有良好的浏览器兼容性和未来发展趋势，Vue 团队希望通过采用最新的语言特性来提升框架的性能和易用性，同时为未来的功能扩展打下坚实的基础。

总之，Vue3.0 通过采用 Proxy API，不仅提升了响应式系统的性能，还改善了代码的简洁性和可维护性，顺应了现代 JavaScript 开发的趋势。

### 说说Vue 3.0中Treeshaking特性? 举例说明—下?

Vue 3.0 中的 Treeshaking 特性是指在构建过程中，通过分析模块之间的依赖关系，移除那些在实际运行时未被引用的代码，从而减少最终输出的 JavaScript 包体积的一种优化手段。Treeshaking 能够确保只有真正被应用使用的代码才会被打包进最终的 bundle 文件中，消除了 dead code（死代码）。

**举例说明**：

假设在 Vue 3.0 的项目中，你有以下两个模块：

```javascript
// utils.js
export function utilityFunction1() {
    ...
} // 实际项目中并未使用
export function utilityFunction2() {
    ...
} // 项目中某个组件正在使用

// MyComponent.vue
import {
    utilityFunction2
} from './utils.js'
export default {
    setup() {
        return {
            doSomething() {
                utilityFunction2();
            }
        };
    }
};
```

在上面的例子中， `utils.js` 文件导出了两个函数，但在 `MyComponent.vue` 中我们只导入并使用了 `utilityFunction2` 。在启用 Treeshaking 的情况下，构建工具（如 Rollup 或 Webpack）会分析出 `utilityFunction1` 并未被任何地方引用，因此在打包过程中，它会被安全地忽略，不会被包含在最终的 bundle 文件中。这样一来，用户下载的应用程序代码量会变得更小，有助于提高应用的加载速度和总体性能。
