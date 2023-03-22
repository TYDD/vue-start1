---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## vue入门开发分享
  面向初学者的vue入门分享.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
---

# Welcome to Vue

vue入门分享

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    START <carbon:arrow-right class="inline"/>
  </span>
</div>

---
transition: fade-out
---

# What is Vue?

Vue (发音为 /vjuː/，类似 view) 是一款用于构建用户界面的 JavaScript 框架。它基于标准 HTML、CSS 和 JavaScript 构建，并提供了一套声明式的、组件化的编程模型，帮助你高效地开发用户界面。

- 📝 **声明式渲染** - Vue 基于标准 HTML 拓展了一套模板语法，使得我们可以声明式地描述最终输出的 HTML 和 JavaScript 状态之间的关系。
- 🎨 **响应式编程** - Vue 会自动跟踪 JavaScript 状态并在其发生变化时响应式地更新 DOM。
- 🛠 **单文件组件SFC（组件化）** - Vue 的单文件组件会将一个组件的逻辑 (JavaScript)，模板 (HTML) 和样式 (CSS) 封装在同一个文件里。实现了封装和重用，且组件间可以相互嵌套。
- 🧑‍💻 **轻量级** - 相对于其他框架，Vue学习成本低，简单易上手。
- 🤹 **虚拟 DOM** - 虚拟 dom 中存在 diff算法，是 cpu 密集型运算，占用内存较少，可以提高运行效率，并压缩运行时体积。
- 📤 **单页面应用（SPA）** - 用户体验好，内容改变时不需要重新加载整个页面，不会进行多个 html 页面间的切换；服务器压力小等。
<br>
<br>

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

</style>

<!--
Here is another comment.
-->

---
transition: slide-up
---

## 总览

```
一个 Vue 单文件组件 (SFC)，通常使用 *.vue 作为文件扩展名，
每一个 *.vue 文件都由三种顶层语言块构成：<template>、<script> 和 <style>，以及一些其他的自定义块

```
```ts {all|2|1-6|9|all}
<template>
  <div class="example">{{ msg }}</div>
</template>

<script>
export default {
  data() {
    return {
      msg: 'Hello world!'
    }
  }
}
</script>

<style>
.example {
  color: red;
}
</style>

<custom1>
  This could be e.g. documentation for the component.
</custom1>

```

<style>
h2 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  font-size: 22px;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

</style>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# API 风格

Vue 的组件可以按两种不同的风格书写

### 选项式 API 和组合式 API

|     |     |
| --- | --- |
| <kbd>选项式 API (Options API)</kbd> | 选项所定义的属性都会暴露在函数内部的 this 上，它会指向当前的组件实例。 |
| <kbd>组合式 API (Composition API) </kbd> | 通过组合式 API，可以使用导入的 API 函数来描述组件逻辑。 |

<!-- https://sli.dev/guide/animations.html#click-animations -->
<img
  v-click
  class="absolute -bottom-9 -left-7 w-80 opacity-50"
  src="https://sli.dev/assets/arrow-bottom-left.svg"
/>
<p v-after class="absolute bottom-23 left-45 opacity-30 transform -rotate-10">Here!</p>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

## 选项式 API (Options API)

-  **状态选项** (data props computed methods watch....)
-  **渲染选项** (data props computed methods watch....)
-  **生命周期选项** (beforeCreate created beforeMount mounted ....)
-  **组合选项** (provide inject mixins extends )
-  **组件实例** ($refs $nextTick $data $props $el....)
-  **其他杂项** (name components directives ....)

<style>
h2 {
  background-color: #2B90B6;
  font-size:22px;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 状态选项

<style>
h1 {
  background-color: #2B90B6;
  text-align: center;
  line-height: 10 !important;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
---
## data

用于声明组件初始响应式状态的函数

```ts

export default {
  data() {
    return { a: 1 }
  },
  created() {
    console.log(this.a) // 1
    console.log(this.$data) // { a: 1 }
  }
}

```

<style>
h2 {
  background-color: #2B90B6;
  font-size:22px;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
---
## props

用于声明一个组件的 props。

<div grid="~ cols-2 gap-2" m="-t-2">

```ts
// 简易声明

export default {
  props: ['size', 'myMessage']
}

```

```ts
// 对象声明，带有验证

export default {
  props: {
    // 类型检查
    height: Number,
    // 类型检查 + 其他验证
    age: {
      type: Number,
      default: 0,
      required: true,
      validator: (value) => {
        return value >= 0
      }
    }
  }
}

```
</div>

<style>
h2 {
  background-color: #2B90B6;
  font-size:22px;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# emits

用于声明由组件触发的自定义事件。

```ts

export default {
  emits: ['check'],
  created() {
    this.$emit('check')
  }
}

```

---
transition: slide-up
---

## computed

用于声明要在组件实例上暴露的计算属性。

<div>

```ts
export default {
  data() {
    return { a: 1 }
  },
  computed: {
    aDouble() { // 只读
      return this.a * 2
    },
    aPlus: { // 可写
      get() {
        return this.a + 1
      },
      set(v) {
        this.a = v - 1
      }
    }
  },
  created() {
    console.log(this.aDouble) // => 2
    console.log(this.aPlus) // => 2
    this.aPlus = 3
    console.log(this.a) // => 2
    console.log(this.aDouble) // => 4
  }
}

```
</div>

---

## methods

用于声明要混入到组件实例中的方法

<div>


```ts

export default {
  data() {
    return { a: 1 }
  },
  methods: {
    plus() {
      this.a++
    }
  },
  created() {
    this.plus()
    console.log(this.a) // => 2
  }
}

```
</div>

---
layout: image-right
image: https://cn.vuejs.org/assets/lifecycle.16e4c08e.png
---
# 生命周期选项

<style>
h1 {
  background-color: #2B90B6;
  text-align: center;
  line-height: 10 !important;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>
---

# beforeCreate
<div>
会在实例初始化完成、props 解析之后、data() 和 computed 等选项处理之前立即调用。

注意，组合式 API 中的 setup() 钩子会在所有选项式 API 钩子之前调用，beforeCreate() 也不例外。
</div>

# created
<div>
当这个钩子被调用时，以下内容已经设置完成：响应式数据、计算属性、方法和侦听器。然而，此时挂载阶段还未开始，因此 $el 属性仍不可用。
</div>

---

# beforeMount
<div>
当这个钩子被调用时，组件已经完成了其响应式状态的设置，但还没有创建 DOM 节点。它即将首次执行 DOM 渲染过程。
</div>

# mounted
<div>
在组件被挂载之后调用。

这个钩子通常用于执行需要访问组件所渲染的 DOM 树相关的副作用
</div>

---
layout: image-right
image: https://img2018.cnblogs.com/blog/1241025/201902/1241025-20190216100154238-1712062934.png
---
# 内置指令

<style>
h1 {
  background-color: #2B90B6;
  text-align: center;
  line-height: 10 !important;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# v-show

v-show 通过设置内联样式的 display CSS 属性来工作，当元素可见时将使用初始 display 值。当条件改变时，也会触发过渡效果。

```ts

<h1 v-show="true">Hello!</h1>

```

# v-if

基于表达式值的真假性，来条件性地渲染元素或者模板片段。

```ts

<h1 v-if="true">Hello!</h1>

```

# v-for

基于原始数据多次渲染元素或模板块。
v-for 的默认方式是尝试就地更新元素而不移动它们。要强制其重新排序元素，你需要用特殊 attribute key 来提供一个排序提示

```ts

<div v-for="item in items" :key="item.id">
  {{ item.text }}
</div>

```

---

# v-if & v-else & v-else-if

三者可以进行链式调用

```ts 

<div v-if="type === 'A'">
  A
</div>
<div v-else-if="type === 'B'">
  B
</div>
<div v-else-if="type === 'C'">
  C
</div>
<div v-else>
  Not A/B/C
</div>


```

---

# v-on
给元素绑定事件监听器。（缩写：@）

<div grid="~ cols-2 gap-2" m="-t-2">

<div>

```ts
<button v-on:click="doThis"></button>

<!-- 监听点击 -->
<button @click="doThis"></button>

<!-- 监听键盘 -->
<input @keyup="onEnter" />

<!-- 停止传播 -->
<button @click.stop="doThis"></button>

<!-- 阻止默认事件 -->
<button @click.prevent="doThis"></button>

<!-- 不带表达式地阻止默认事件 -->
<form @submit.prevent></form>

<!-- 链式调用修饰符 -->
<button @click.stop.prevent="doThis"></button>


```
</div>

<div>

```ts
.stop - 调用 event.stopPropagation()。
.prevent - 调用 event.preventDefault()。
.capture - 在捕获模式添加事件监听器。
.self - 只有事件从元素本身发出才触发处理函数。
.{keyAlias} - 只在某些按键下触发处理函数。
.once - 最多触发一次处理函数。
.left - 只在鼠标左键事件触发处理函数。
.right - 只在鼠标右键事件触发处理函数。
.middle - 只在鼠标中键事件触发处理函数。
.passive - 通过 { passive: true } 附加一个 DOM 事件。

```
</div>

</div>

---

# v-bind

动态的绑定一个或多个 attribute，也可以是组件的 prop。 (缩写 : 或者 .)

<div grid="~ cols-2 gap-2" m="-t-2">
<div>

```ts
  <!-- 绑定 attribute -->
  <img v-bind:src="imageSrc" />
  <!-- 缩写 -->
  <img :src="imageSrc" />
  <!-- 绑定对象形式的 attribute -->
  <div v-bind="{ id: someProp}"></div>
  <!-- class 绑定 -->
  <div :class="{ red: isRed }"></div>
  <div :class="[classA, classB]"></div>
  <div :class="[classA, { classB: isB}]"></div>
  <!-- style 绑定 -->
  <div :style="{ fontSize: size + 'px' }"></div>
  <div :style="[styleObjectA, styleObjectB]"></div>

```
</div>

<div>

```ts
<!-- prop 绑定。“prop” 必须在子组件中已声明。 -->
<MyComponent :prop="someThing" />

<!-- 传递子父组件共有的 prop -->
<MyComponent v-bind="$props" />

```
</div>

</div>

---

# v-model

在表单输入元素或组件上创建双向绑定。

```ts
// 仅限于
<input>
<select>
<textarea>
...
components

```

```ts

<input v-model="searchText" />

// 等同于
<input
  :value="searchText"
  @input="searchText = $event.target.value"
/>
// 自定义组件实现双向绑定
<CustomInput
  v-model="searchText"
/>
<CustomInput
  :value="searchText"
  @input="newValue => searchText = newValue"
/>

```
---

# 回顾

- **vue 是什么**
- **声明式渲染**
- **选项式 API**
- **Attribute 绑定**
- **事件监听**
- **表单绑定以及双向绑定**
- **条件渲染**
- **列表渲染**
- **计算属性**
- **生命周期函数**
- **Props**
- **Emits**

<!-- https://cn.vuejs.org/examples/#hello-world -->

---

# 实现todoList

```html
<TodoList :todoList="['默认任务']" />
```

<!-- ./components/TodoList.vue -->
<TodoList :todoList="['默认任务']"/>