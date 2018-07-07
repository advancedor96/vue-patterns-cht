# Vue 實作模式 (vue-patterns) 中文版

英文原版：[learn-vuejs](https://github.com/learn-vuejs/vue-patterns)  
中文翻譯：[yoyoys](https://github.com/yoyoys)

此頁面集結了許多有用的 Vue 實作模式、技術、技巧、以及有幫助的參考連結。

- [Vue 實作模式 (learn-vuejs) 中文版](#vue-%E5%AF%A6%E4%BD%9C%E6%A8%A1%E5%BC%8F-learn-vuejs-%E4%B8%AD%E6%96%87%E7%89%88)
  - [元件宣告](#%E5%85%83%E4%BB%B6%E5%AE%A3%E5%91%8A)
    - [單文件組件(Single File Component, SFC) - 最為常見](#%E5%96%AE%E6%96%87%E4%BB%B6%E7%B5%84%E4%BB%B6single-file-component-sfc---%E6%9C%80%E7%82%BA%E5%B8%B8%E8%A6%8B)
    - [字串樣板 (String Template) (或是 es6 樣板字面值 (Template Literal)))](#%E5%AD%97%E4%B8%B2%E6%A8%A3%E6%9D%BF-string-template-%E6%88%96%E6%98%AF-es6-%E6%A8%A3%E6%9D%BF%E5%AD%97%E9%9D%A2%E5%80%BC-template-literal)
    - [渲染函式 (Render Function)](#%E6%B8%B2%E6%9F%93%E5%87%BD%E5%BC%8F-render-function)
    - [JSX](#jsx)
    - [vue-class-component (使用 es6 classes)](#vue-class-component-%E4%BD%BF%E7%94%A8-es6-classes)
      - [參考連結](#%E5%8F%83%E8%80%83%E9%80%A3%E7%B5%90)
  - [元件之間的溝通（Component Communication）](#%E5%85%83%E4%BB%B6%E4%B9%8B%E9%96%93%E7%9A%84%E6%BA%9D%E9%80%9Acomponent-communication)
    - [屬性與事件（Props and Events）](#%E5%B1%AC%E6%80%A7%E8%88%87%E4%BA%8B%E4%BB%B6props-and-events)
  - [元件事件處理方法（Component Events Handling）](#%E5%85%83%E4%BB%B6%E4%BA%8B%E4%BB%B6%E8%99%95%E7%90%86%E6%96%B9%E6%B3%95component-events-handling)
  - [元件條件渲染 (Component Conditional Rendering)](#%E5%85%83%E4%BB%B6%E6%A2%9D%E4%BB%B6%E6%B8%B2%E6%9F%93-component-conditional-rendering)
    - [指令 (Directives) (`v-if` / `v-else` / `v-else-if` / `v-show`)](#%E6%8C%87%E4%BB%A4-directives-v-if--v-else--v-else-if--v-show)
    - [JSX](#jsx)
  - [動態元件](#%E5%8B%95%E6%85%8B%E5%85%83%E4%BB%B6)
  - [元件組合](#%E5%85%83%E4%BB%B6%E7%B5%84%E5%90%88)
    - [基本組合 (Basic Composition)](#%E5%9F%BA%E6%9C%AC%E7%B5%84%E5%90%88-basic-composition)
    - [繼承 (Extends)](#%E7%B9%BC%E6%89%BF-extends)
    - [混入 (Mixins)](#%E6%B7%B7%E5%85%A5-mixins)
    - [預設插槽 (Slots (Default))](#%E9%A0%90%E8%A8%AD%E6%8F%92%E6%A7%BD-slots-default)
    - [具名插槽(Named Slots)](#%E5%85%B7%E5%90%8D%E6%8F%92%E6%A7%BDnamed-slots)
    - [作用域插槽 (Scoped Slots)](#%E4%BD%9C%E7%94%A8%E5%9F%9F%E6%8F%92%E6%A7%BD-scoped-slots)
    - [渲染屬性 (Render Props)](#%E6%B8%B2%E6%9F%93%E5%B1%AC%E6%80%A7-render-props)
  - [參數傳遞 (Passing Props)](#%E5%8F%83%E6%95%B8%E5%82%B3%E9%81%9E-passing-props)
  - [高優先元件 (Higher Order Component, HOC)](#%E9%AB%98%E5%84%AA%E5%85%88%E5%85%83%E4%BB%B6-higher-order-component-hoc)
  - [相依注入 (Dependency injection)](#%E7%9B%B8%E4%BE%9D%E6%B3%A8%E5%85%A5-dependency-injection)
    - [**提供** 與 **注入** (Provide / Inject)](#%E6%8F%90%E4%BE%9B-%E8%88%87-%E6%B3%A8%E5%85%A5-provide--inject)
    - [注入裝飾器模式 (@Provide / @Inject Decorator)](#%E6%B3%A8%E5%85%A5%E8%A3%9D%E9%A3%BE%E5%99%A8%E6%A8%A1%E5%BC%8F-provide--inject-decorator)
  - [錯誤處理 (Handling Errors)](#%E9%8C%AF%E8%AA%A4%E8%99%95%E7%90%86-handling-errors)
    - [`errorCaptured` 事件](#errorcaptured-%E4%BA%8B%E4%BB%B6)
  - [生產力小技巧](#%E7%94%9F%E7%94%A2%E5%8A%9B%E5%B0%8F%E6%8A%80%E5%B7%A7)
  - [有用的連結](#%E6%9C%89%E7%94%A8%E7%9A%84%E9%80%A3%E7%B5%90)
    - [重構技巧](#%E9%87%8D%E6%A7%8B%E6%8A%80%E5%B7%A7)
    - [狀態管理](#%E7%8B%80%E6%85%8B%E7%AE%A1%E7%90%86)
    - [Vuex](#vuex)
    - [Mobx](#mobx)
    - [不須渲染的元件 (Renderless Component)](#%E4%B8%8D%E9%A0%88%E6%B8%B2%E6%9F%93%E7%9A%84%E5%85%83%E4%BB%B6-renderless-component)
    - [目錄結構](#%E7%9B%AE%E9%8C%84%E7%B5%90%E6%A7%8B)
    - [小技巧](#%E5%B0%8F%E6%8A%80%E5%B7%A7)
    - [路由（Router）](#%E8%B7%AF%E7%94%B1Router)
    - [不良示範 (反模式)](#%E4%B8%8D%E8%89%AF%E7%A4%BA%E7%AF%84-%E5%8F%8D%E6%A8%A1%E5%BC%8F)
    - [影片與音訊課程](#%E5%BD%B1%E7%89%87%E8%88%87%E9%9F%B3%E8%A8%8A%E8%AA%B2%E7%A8%8B)
    - [專案範例](#%E5%B0%88%E6%A1%88%E7%AF%84%E4%BE%8B)
    - [付費課程](#%E4%BB%98%E8%B2%BB%E8%AA%B2%E7%A8%8B)
    - [Typescript](#typescript)
    - [Flowtype](#flowtype)
    - [GraphQL](#graphql)
    - [其他資訊](#%E5%85%B6%E4%BB%96%E8%B3%87%E8%A8%8A)

## 元件宣告

### 單文件組件(Single File Component, SFC) - 最為常見

```html
<template>
  <button class="btn-primary" @click.prevent="handleClick">
    {{text}}
  </button>
</template>

<script>
export default {
  data() {
    return {
      text: 'Click me',
    };
  },
  methods: {
    handleClick() {
      console.log('clicked');
    },
  },
}
</script>

<style scoped>
.btn-primary {
  background-color: blue;
}
</style>
```

### 字串樣板 (String Template) (或是 es6 樣板字面值 (Template Literal))

```js
Vue.component('my-btn', {
  template: `
    <button class="btn-primary" @click.prevent="handleClick">
      {{text}}
    </button>
  `,
  data() {
    return {
      text: 'Click me',
    };
  },
  methods: {
    handleClick() {
      console.log('clicked');
    },
  },
});
```

### 渲染函式 (Render Function)

```js
Vue.component('my-btn', {
  data() {
    return {
      text: 'Click me',
    };
  },
  methods: {
    handleClick() {
      console.log('clicked');
    },
  },
  render(h) {
    return h('button', {
      attrs: {
        class: 'btn-primary'
      },
      on: {
        click: this.handleClick,
      },
    });
  },
});
```

### JSX

```jsx
Vue.component('my-btn', {
  data() {
    return {
      text: 'Click me',
    };
  },
  methods: {
    handleClick() {
      console.log('clicked');
    },
  },
  render() {
    return (
      <button class="btn-primary" onClick={this.handleClick}>
        {{this.text}}
      </button>
    );
  },
});
```

### [vue-class-component](https://github.com/vuejs/vue-class-component) (使用 es6 classes)

```html
<template>
  <button class="btn-primary" @click.prevent="handleClick">
    {{text}}
  </button>
</template>

<script>
import Vue from 'vue';
import Component from 'vue-class-component';

@Component
export default MyBtn extends Vue {
  text = 'Click me';

  handleClick() {
    console.log('clicked');
  }
}
</script>

<style scoped>
.btn-primary {
  background-color: blue;
}
</style>
```

#### 參考連結

* [7 Ways To Define A Component Template in VueJS](https://medium.com/js-dojo/7-ways-to-define-a-component-template-in-vuejs-c04e0c72900d)

## 元件之間的溝通（Component Communication）

### 屬性與事件（Props and Events）

基本上，Vue 元件是依照單向資料流傳遞資料，這就是屬性進、事件出（props down, event up）[請參考官方說明](https://vuejs.org/v2/guide/components-props.html#One-Way-Data-Flow)）。
（譯註：也有稱作props in, emit out。）
屬性（props）是唯讀的資料，所以不可能從子元件內部修改他的值，若是外部傳入的屬性變化了，子元件將會自動重繪（因為屬性是反應性資料）。
子元件只能將事件發送到父代，藉此父代可以修改資料（`data`） ，這個資料也對應到子元件的屬性（`props`）。

```html
<template>
  <button @click="$emit('click')">{{text}}</button>
</template>

<script>
export default {
  name: 'v-btn',
  props: {
    text: String,
  },
};
</script>
```

```html
<template>
  <v-btn :text="buttonText" @click="handleClick"></v-btn>
</template>

<script>
export default {
  data() {
    return {
      clickCount: 0,
      buttonText: 'initial button text',
    };
  },
  methods: {
    handleClick() {
      this.buttonText = `Button clicked ${++this.clickCount}`;
      console.log('clicked', this.buttonText);
    }
  }
};
</script>
```

#### 參考連結:

 [Vue.js Component Communication Patterns](https://alligator.io/vuejs/component-communication/)
* [Creating Custom Inputs With Vue.js]https://www.smashingmagazine.com/2017/08/creating-custom-inputs-vue-js/)
* [Vue Sibling Component Communication](https://vegibit.com/vue-sibling-component-communication/)
* [Managing State in Vue.js](https://medium.com/fullstackio/managing-state-in-vue-js-23a0352b1c87)

## 元件事件處理方法（Component Events Handling）

#### 參考連結:

* [Leveraging Vue events to reduce prop declarations](https://itnext.io/leveraging-vue-events-to-reduce-prop-declarations-e38f5dce2aaf)
* [Vue.js Component Hooks as Events](https://alligator.io/vuejs/component-event-hooks/)
* [Creating a Global Event Bus with Vue.js](https://alligator.io/vuejs/global-event-bus/)
* [Vue.js Event Bus + Promises](https://medium.com/@jesusgalvan/vue-js-event-bus-promises-f83e73a81d72)

## 元件條件渲染 (Component Conditional Rendering)

### 指令 (Directives) (`v-if` / `v-else` / `v-else-if` / `v-show`)

`v-if`

```html
<h1 v-if="true">只在 v-if 值為 true 時渲染</h1>
```

`v-if` 與 `v-else`

```html
<h1 v-if="true">只在 v-if 值為 true 時渲染</h1>
<h1 v-else>只在 v-if 值為 false 時渲染</h1>
```

`v-else-if`

```html
<div v-if="type === 'A'">只在 `type` 等於 `A` 時渲染</div>
<div v-else-if="type === 'B'">只在 `type` 等於 `B` 時渲染</div>
<div v-else-if="type === 'C'">只在 `type` 等於 `C` 時渲染</div>
<div v-else>只在 `type` 不等於>fmf `A` 或 `B` 或 `C` 時渲染</div>
```

`v-show`

```html
<h1 v-show="true">永遠都會渲染，但是只在 `v-show` 值為 true 時顯示</h1>
```

如果你需要同時在多個元素上面做條件式渲染，你可以在 `<template>` 元素上使用這些指令 (`v-if` / `v-else` / `v-else-if` /`v-show`)。
注意：`<template>` 元素不會實際渲染一個 DOM。

```html
<template v-if="true">
  <h1>所有元素</h1>
  <p>都會被渲染成為 DOM</p>
  <p>除了 `template` 元素</p>
</template>
```

### JSX

如果你在你的 Vue 應用程式中使用 JSX，你可以使用所有 javascript 語句，例如 `if else` 、 `switch case` 、三元運算 (`ternary`) 與 邏輯運算式 (logical operator)

`if else` 語句

```jsx
export default {
  data() {
    return {
      isTruthy: true,
    };
  },
  render(h) {
    if (this.isTruthy) {
      return <h1>值為真時渲染</h1>;
    } else {
      return <h1>值為假時渲染</h1>;
    }
  },
};
```

`switch case` 語句

```jsx
import Info from './Info';
import Warning from './Warning';
import Error from './Error';
import Success from './Success';

export default {
  data() {
    return {
      type: 'error',
    };
  },
  render(h) {
    switch (this.type) {
      case 'info':
        return <Info text={text} />;
      case 'warning':
        return <Warning text={text} />;
      case 'error':
        return <Error text={text} />;
      default:
        return <Success text={text} />;
    },
  }
};
```

你也可以透過物件的對應來簡化 `switch case`

```jsx
import Info from './Info';
import Warning from './Warning';
import Error from './Error';
import Success from './Success';

const COMPONENT_MAP = {
  info: Info,
  warning: Warning,
  error: Error,
  success: Success,
};

export default {
  data() {
    return {
      type: 'error',
    };
  },
  render(h) {
    const Comp = COMPONENT_MAP[this.type || 'success'];

    return <Comp />;
  },
};
```

三元運算子 (ternary operator)

```jsx
export default {
  data() {
    return {
      isTruthy: true,
    };
  },
  render(h) {
    return (
      <div>
        {this.isTruthy ? (
          <h1>值為真時渲染</h1>
        ) : (
          <h1>值為假時渲染</h1>
        )}
      </div>
    );
  },
};
```

邏輯運算子 (logical operator)

```jsx
export default {
  data() {
    return {
      isLoading: true,
    };
  },
  render(h) {
    return <div>{this.isLoading && <h1>Loading ...</h1>}</div>;
  },
};
```
#### 參考連結
* [Difference Between v-if and v-show [With Video at End]](https://dzone.com/articles/difference-between-v-if-and-v-show-with-a-video)

## 動態元件

### 使用 `is` 屬性在 `<component>`  元素上

* [範例 1](https://jsfiddle.net/chrisvfritz/o3nycadu/)
* [範例 2](https://jsfiddle.net/chrisvfritz/b2qj69o1/)
* [範例 3](https://alligator.io/vuejs/dynamic-components/)

```html
<component :is="currentTabComponent"></component>
```

上面的範例，原有 `<component>` 中的元件，在切換元件的同時將會被消滅。
如果你需要切換後仍保留 `<component>` 中元件的實體，而不被消滅的話，可以包裹一個 `<keep-alive>` 標籤，如下：

```html
<keep-alive>
  <component :is="currentTabComponent"></component>
</keep-alive>
```
#### 參考連結

* [Dynamic Component Templates with Vue.js](https://medium.com/scrumpy/dynamic-component-templates-with-vue-js-d9236ab183bb)

#### 元件庫

* [Proppy - Functional props composition for components](https://proppyjs.com/)

## 元件組合

### 基本組合 (Basic Composition)

```html
<template>
  <div class="component-b">
    <component-a></component-a>
  </div>
</template>

<script>
import ComponentA from './ComponentA';

export default {
  components: {
    ComponentA,
  },
};
</script>
```

### 繼承 (Extends)

當你需要繼承一個單文件組件 (SFC) 時可以使用。

```html
<template>
  <button class="button-primary" @click.prevent="handleClick">
    {{buttonText}}
  </button>
</template>

<script>
import BaseButton from './BaseButton';

export default {
  extends: BaseButton,
  props: ['buttonText'],
};
</script>
```

#### 參考連結

* [Extending VueJS Components](https://medium.com/js-dojo/extending-vuejs-components-42fefefc688b)

### 混入 (Mixins)

```js
// closableMixin.js
export default {
  props: {
    isOpen: {
      default: true
    }
  },
  data: function() {
    return {
      shown: this.isOpen
    }
  },
  methods: {
    hide: function() {
      this.shown = false;
    },
    show: function() {
      this.shown = true;
    },
    toggle: function() {
      this.shown = !this.shown;
    }
  }
}
```

```html
<template>
  <div v-if="shown" class="alert alert-success" :class="'alert-' + type" role="alert">
    {{text}}
    <i class="pull-right glyphicon glyphicon-remove" @click="hide"></i>
  </div>
</template>

<script>
import closableMixin from './mixins/closableMixin';

export default {
  mixins: [closableMixin],
  props: ['text']
};
</script>
```

#### 參考連結

* [Practical use of Components and Mixins in Vue JS](http://www.qcode.in/practical-use-of-components-and-mixins-in-vue-js/)


### 預設插槽 (Slots (Default))

```html
<template>
  <button class="btn btn-primary">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'VBtn',
};
</script>
```

```html
<template>
  <v-btn>
    <span class="fa fa-user"></span>
    Login
  </v-btn>
</template>

<script>
import VBtn from './VBtn';
  
export default {
  components: {
    VBtn,
  }
};
</script>
```

#### 參考連結

* [Understanding Component Slots with Vue.js](https://alligator.io/vuejs/component-slots/)
* [Composing Custom Elements With Slots And Named Slots](https://alligator.io/web-components/composing-slots-named-slots/)
* [Writing Abstract Components with Vue.js](https://alligator.io/vuejs/vue-abstract-components/)

### 具名插槽(Named Slots)

BaseLayout.vue

```html
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>
```

App.vue

```html
<base-layout>
  <template slot="header">
    <h1>這裡是頁面標題</h1>
  </template>

  <p>一段文件主體內的文字</p>
  <p>另外一段文字</p>

  <template slot="footer">
    <p>一些聯絡資訊</p>
  </template>
</base-layout>
```

### 作用域插槽 (Scoped Slots)

```html
<template>
  <ul>
    <li
      v-for="todo in todos"
      v-bind:key="todo.id"
    >
      <!-- 保留一個插槽供每一個 todo 使用，-->
      <!-- 並將 將 `todo` 物件作為插槽參數傳遞給它，供外部元件使用。-->
      <slot v-bind:todo="todo">
        {{ todo.text }}
      </slot>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    todos: {
      type: Array,
      default: () => ([]),
    }
  },
};
</script>
```

```html
<template>
  <todo-list v-bind:todos="todos">
      <template slot-scope="{ todo }">
        <span v-if="todo.isComplete">✓</span>
        {{ todo.text }}
      </template>
  </todo-list>
</template>

<script>
import TodoList from './TodoList';

export default {
  components: {
    TodoList,
  },
  data() {
    return {
      todos: [
        { todo: 'todo 1', isComplete: true },
        { todo: 'todo 2', isComplete: false },
        { todo: 'todo 3', isComplete: false },
        { todo: 'todo 4', isComplete: true },
      ];
    };
  },
};
</script>
```

#### 參考資料

* [Getting Your Head Around Vue.js Scoped Slots](https://medium.com/js-dojo/getting-your-head-around-vue-js-scoped-slots-281bf82a1e4e)
* [Understanding scoped slots in Vue.js](https://medium.com/corebuild-software/understanding-scoped-slots-in-vue-js-db5315a42391)
* [Scoped Component Slots in Vue.js](https://alligator.io/vuejs/scoped-component-slots/)
* [The Trick to Understanding Scoped Slots in Vue.js](https://adamwathan.me/the-trick-to-understanding-scoped-slots-in-vuejs/)
* [The Power of Scoped Slots in Vue](https://pineco.de/power-scoped-slots-vue/)

### 渲染屬性 (Render Props)

大多數狀況下，你可以優先使用作用域插槽 (Scoped Slots) 之於渲染屬性 (Render Props)，但是，在某些狀況下渲染屬性還是很有用的。

於單文件組件：

```html
<template>
  <div id="app">
    <Mouse :render="__render"/>
  </div>
</template>

<script>
import Mouse from "./Mouse.js";
export default {
  name: "app",
  components: {
    Mouse
  },
  methods: {
    __render({ x, y }) {
      return (
        <h1>
          The mouse position is ({x}, {y})
        </h1>
      );
    }
  }
};
</script>
<style>
* {
  margin: 0;
  height: 100%;
  width: 100%;
}
</style>
```

於 `JSX`

```js
const Mouse = {
  name: "Mouse",
  props: {
    render: {
      type: Function,
      required: true
    }
  },
  data() {
    return {
      x: 0,
      y: 0
    };
  },
  methods: {
    handleMouseMove(event) {
      this.x = event.clientX;
      this.y = event.clientY;
    }
  },
  render(h) {
    return (
      <div style={{ height: "100%" }} onMousemove={this.handleMouseMove}>
        {this.$props.render(this)}
      </div>
    );
  }
};

export default Mouse;
```

#### 參考連結

* [Leveraging Render Props in Vue](https://medium.com/@dillonchanis/leveraging-render-props-in-vue-7eb9a19c262d)
* [Use a Vue.js Render Prop!](https://medium.com/js-dojo/use-a-vue-js-render-prop-98880bc44e05)

## 參數傳遞 (Passing Props)

有時候你想要傳遞所有參數 (props) 與事件 (listeners) 到子元件，但又不想要宣告所有子元件的參數。
你可以直接將 `$attrs` 與 `$listeners` 綁定在子元件上。

```html
<template>
  <div>
    <h1>{{title}}</h1>
    <child-component v-bind="$attrs" v-on="$listeners"></child-component>
  </div>
</template>

<script>
export default {
  name: 'PassingPropsSample'
  props: {
    title: {
      type: String,
      default: 'Hello, Vue!'
    }
  }
};
</script>
```

在父元件上，你可以這樣做：
```html
<template>
  <passing-props-sample
    title="Hello, Passing Props"
    childPropA="This props will properly mapped to <child-component />"
    @click="handleChildComponentClick"
  >
  </passing-props-sample>
</template>

<script>
import PassingPropsSample from './PassingPropsSample';

export default {
  components: {
    PassingPropsSample
  },
  methods: {
    handleChildComponentClick() {
      console.log('child component clicked');
    }
  }
};
</script>
```

#### 參考資料

* [Transparent Wrapper Components in Vue](https://zendev.com/2018/05/31/transparent-wrapper-components-in-vue.html)

## 高優先元件 (Higher Order Component, HOC)

#### 參考連結

* [Higher Order Components in Vue.js](https://medium.com/bethink-pl/higher-order-components-in-vue-js-a79951ac9176)
* [Do we need Higher Order Components in Vue.js?](https://medium.com/bethink-pl/do-we-need-higher-order-components-in-vue-js-87c0aa608f48)
* [Higher-Order Components in Vue.js](https://medium.com/tldr-tech/higher-order-components-in-vue-js-38b500c6d49f)

## 相依注入 (Dependency injection)

Vue 支援 **提供** 與 **注入** (Provide / inject) 機制來傳遞一個物件到所有子代元件中，不管結構有多深，只要都基於同一個父代即可。
注意： `provide` 和 `inject` 並沒有響應能力 (reactive) ，除非你傳遞的物件本身就帶有響應能力。

```html
<parent-component>  // 父元件
  <child-component>  // 子元件
    <grand-child-component></grand-child-component>  // 孫元件
  </child-component>
</parent-component>
```

上述的元件結構，若要從 `父元件` 取得資料，你必須要透過 參數(`props`) 傳遞資料到 `子元件` 與 `孫元件` 之中。
但如果 `父元件` **提供** (`provide`) 資料（或物件）， `孫元件` 可以透過宣告直接 **注入** (`inject`)  `父元件`  中所定義的資料（或物件）。


#### 參考連結

* [Official API](https://vuejs.org/v2/api/#provide-inject)
* [Official Guide](https://vuejs.org/v2/guide/components-edge-cases.html#Dependency-Injection)
* [Component Communication](https://alligator.io/vuejs/component-communication/#provide--inject)
* [Dependency Injection in Vue.js App with TypeScript](https://blog.kloud.com.au/2017/03/22/dependency-injection-in-vuejs-app-with-typescript/)

### **提供** 與 **注入** (Provide / Inject)

```js
// ParentComponent.vue

export default {
  provide: {
    theme: {
      primaryColor: 'blue',
    },
  },
};
```

```html
// GrandChildComponent.vue

<template>
  <button :style="{ backgroundColor: primary && theme.primaryColor }">
    <slot></slot>
  </button>
</template>

<script>
export default {
  inject: ['theme'],
  props: {
    primary: {
      type: Boolean,
      default: true,
    },
  },
};
</script>
```

### 注入裝飾器模式 ([@Provide / @Inject Decorator](https://github.com/kaorun343/vue-property-decorator))

```js
// ParentComponent.vue

import { Component, Vue, Provide } from 'vue-property-decorator';

@Component
export class ParentComponent extends Vue {
  @Provide
  theme = {
    primaryColor: 'blue',
  };
}
```

```html
// GrandChildComponent.vue

<template>
  <button :style="{ backgroundColor: primary && theme.primaryColor }">
    <slot></slot>
  </button>
</template>

<script>
import { Component, Vue, Inject, Prop } from 'vue-property-decorator';

export class GrandChildComponent extends Vue {
  @Inject() theme;

  @Prop({ default: true })
  primary: boolean;
};
</script>
```

## 錯誤處理 (Handling Errors)

### `errorCaptured` 事件

```js
export default {
  name: 'ErrorBoundary',
  data() {
    return {
      error: false,
      errorMessage: '',
    };
  },
  errorCaptured (err, vm, info) {
    this.error = true;
    this.errorMessage = `${err.stack}\n\nfound in ${info} of component`;
    
    return false;
  },
  render (h) {
    if (this.error) {
      return h('pre', { style: { color: 'red' }}, this.errorMessage);
    }

    return this.$slots.default[0]
  }
};
```

```
<error-boundary>
  <another-component/>
</error-boundary>
```

#### 範例

* [Example 1](https://jsfiddle.net/Linusborg/z84wspcg/)

#### 參考連結

* [Handling Errors in Vue with Error Boundaries](https://medium.com/@dillonchanis/handling-errors-in-vue-with-error-boundaries-91f6ead0093b)

## 生產力小技巧

讓監聽器在 created 事件時就有效

```js
// 不要這樣做
created() {
  this.fetchUserList();
},
watch: {
  searchText: 'fetchUserList',
}
```

```js
// 這樣做
watch: {
  searchText: {
    handler: 'fetchUserList',
    immediate: true,
  }
}
```

## 有用的連結

### 風格指南
* [Official - Style Guide](https://vuejs.org/v2/style-guide/)
* [Vue.js Component Style Guide](https://github.com/pablohpsilva/vuejs-component-style-guide)

### 重構技巧

* [Refactoring Vue: Cleaning Up a List of Posts With Better Component Splitting and More ES6](https://mattstauffer.com/blog/refactoring-vue-cleaning-up-a-list-of-posts-with-better-component-splitting-and-more-es6/?utm_campaign=Revue%20newsletter&utm_medium=Newsletter&utm_source=Vue.js%20Feed)
* [Clean up your Vue modules with ES6 Arrow Functions](https://gist.github.com/JacobBennett/7b32b4914311c0ac0f28a1fdc411b9a7)
* [Examples of Vue’s Clean Code](https://webdesign.tutsplus.com/tutorials/examples-of-vues-clean-code--cms-29619)
* [Optimizing Performance with Computed Properties](https://codingexplained.com/coding/front-end/vue-js/optimizing-performance-computed-properties)

### 狀態管理

* [Managing State in Vue.js](https://medium.com/fullstackio/managing-state-in-vue-js-23a0352b1c87)


### Vuex

* [Decouple Vuex modules with the Mediator pattern](https://itnext.io/decouple-vuex-actions-with-the-mediator-pattern-58a8879de1b4)
* [Vuex getters are great, but don’t overuse them](https://codeburst.io/vuex-getters-are-great-but-dont-overuse-them-9c946689b414)
* [Reusable Vuex Mutation Functions](https://itnext.io/reusable-vuex-mutation-functions-9b4920aa737b)
* [A pattern to handle ajax requests in Vuex](https://medium.com/@lachlanmiller_52885/a-pattern-to-handle-ajax-requests-in-vuex-2d69bc2f8984)
* [[vuex Mutations] Single Changes vs. Single Responsibility](https://forum.vuejs.org/t/vuex-mutations-single-changes-vs-single-responsibility/16396)
* [Components and How They Interact in Vue and Vuex](https://dzone.com/articles/how-do-components-interact-in-vue-and-what-is-vuex)
* [Why VueX Is The Perfect Interface Between Frontend and API](https://codeburst.io/why-vuex-is-the-perfect-interface-between-frontend-and-api-271d92161709)
* [Composing actions with Vuex](https://codeburst.io/composing-actions-with-vuex-b63466264a37)
* [How to Build Complex, Large-Scale Vue.js Apps With Vuex](https://code.tutsplus.com/tutorials/how-to-build-complex-large-scale-vuejs-applications-with-vuex--cms-30952)
* [Should I Store This Data in Vuex?](https://markus.oberlehner.net/blog/should-i-store-this-data-in-vuex/)
### Mobx

* [Build A View-Framework-Free Data Layer Based on MobX — Integration With Vue (1)](https://itnext.io/build-a-view-framework-free-data-layer-based-on-mobx-integration-with-vue-1-8b524b86c7b8)

### 不須渲染的元件 (Renderless Component)

* [Renderless Components in Vue.js](https://adamwathan.me/renderless-components-in-vuejs/)
* [Building Renderless Components to Handle CRUD Operations in Vue.js](https://markus.oberlehner.net/blog/building-renderless-components-to-handle-crud-operations-in-vue/)

#### 範例

* [Renderless Calendar component](https://codesandbox.io/s/v65lx0xvy5)

### 目錄結構

* [How you can improve your workflow using the JavaScript console](https://medium.freecodecamp.org/how-you-can-improve-your-workflow-using-the-javascript-console-bdd7823a9472)
* [How to Structure a Vue.js Project](https://itnext.io/how-to-structure-a-vue-js-project-29e4ddc1aeeb)
* [Large-scale Vuex application structures](https://medium.com/3yourmind/large-scale-vuex-application-structures-651e44863e2f)
* [Vue.js Application Structure and CSS Architecture](https://markus.oberlehner.net/blog/vue-application-structure-and-css-architecture/)

### 小技巧

* [How To Build Vue Components Like A Pro 😎](https://blog.bitsrc.io/how-to-build-vue-components-like-a-pro-fd89fd4d524d)
* [Four tips for working with Vue.js](https://itnext.io/four-tips-for-working-with-vue-js-b362d97de852)
* [Tips from a Lowly VueJS Developer](https://medium.com/@denny.headrick/tips-from-a-lowly-vuejs-developer-381b6956aece)
* [Throttling and Debouncing Events with Vue.js and lodash](https://alligator.io/vuejs/lodash-throttle-debounce/)
* [Are partially applied functions in event handlers possible?](https://forum.vuejs.org/t/are-partially-applied-functions-in-event-handlers-possible/10187)
* [Vue.js — Considerations and Tricks](https://blog.webf.zone/vue-js-considerations-and-tricks-fa7e0e4bb7bb)
* [Six random issues and their solutions in VueJS.](https://medium.com/@stijlbreuk/six-random-issues-and-their-solutions-in-vuejs-b16d470a6462)
* [When VueJS Can't Help You](https://vuejsdevelopers.com/2017/05/01/vue-js-cant-help-head-body/)
* [Things that won’t work using Vue](https://winnercrespo.com/things-that-wont-work-using-vue/)
* [Tip#15 Delay execution with _.debounce](https://medium.com/vuejs-tips/tip-15-delay-execution-with-debounce-6a93b759bb06)

### 路由（Router）

* [Navigation Guards - Official](https://router.vuejs.org/guide/advanced/navigation-guards.html#global-guards)
* [Vue Router Navigation Guards with Vuex](https://serversideup.net/vue-router-navigation-guards-vuex/)

### 不良示範 (反模式)

* [Chris Fritz - Vue.js Anti-Patterns (and How to Avoid Them)](http://www.fullstackradio.com/87)
* [Common mistakes to avoid while working with Vue.js](https://medium.freecodecamp.org/common-mistakes-to-avoid-while-working-with-vue-js-10e0b130925b)
* [Avoid This Common Anti-Pattern In Full-Stack Vue/Laravel Apps](https://vuejsdevelopers.com/2017/08/06/vue-js-laravel-full-stack-ajax/)
* [[Video] - VueNYC - Three Vue code smells, and what you can do about them - Matt Rothenberg (@mattrothenberg)](https://www.youtube.com/watch?v=z5UWVOeIsUQ)

### 影片與音訊課程

* [81: Evan You - Advanced Vue Component Design](https://player.fm/series/series-1401837/81-evan-you-advanced-vue-component-design)
* [7 Secret Patterns Vue Consultants Don’t Want You to Know](https://www.youtube.com/watch?v=7YZ5DwlLSt8)

### 專案範例

* [vue-enterprise-boilerplate](https://github.com/chrisvfritz/vue-enterprise-boilerplate)
* [7-secret-patterns](https://github.com/chrisvfritz/7-secret-patterns)
* [Vue.js-2-Design-Patterns-and-Best-Practices](https://github.com/PacktPublishing/Vue.js-2-Design-Patterns-and-Best-Practices)

### 付費課程

* [Advanced Vue Component Design](https://adamwathan.me/advanced-vue-component-design/)
* [Advanced Vue.js Features from the Ground Up](https://frontendmasters.com/courses/advanced-vue/)


### Typescript

* [Vue + TypeScript: A Match Made in Your Code Editor](https://css-tricks.com/vue-typescript-a-match-made-in-your-code-editor/)
* [Writing Class-Based Components with Vue.js and TypeScript](https://alligator.io/vuejs/typescript-class-components/)

### Flowtype

### GraphQL

---

### 其他資訊


* [Creating an Interpose Vue component from a React implementation](https://itnext.io/creating-an-interpose-vue-component-from-a-react-implementation-80d367a695c6)
* [Composing computed properties in Vue.js](https://medium.com/@kevin_peters/composing-computed-properties-in-vue-js-87b4507af079)
* [4 AJAX Patterns For Vue.js Apps](https://medium.com/js-dojo/4-ajax-patterns-for-vue-js-apps-add915fc9168)
* [3 Code Splitting Patterns For VueJS and Webpack](https://medium.com/js-dojo/3-code-splitting-patterns-for-vuejs-and-webpack-b8fff1ea0ba4)
* [The easiest way to improve your Vue.js application. Part 1](https://codeburst.io/the-easiest-way-to-improve-your-vue-js-application-part-1-51f068652872)
* [Using JSX with Vue and Why You Should Care](https://scotch.io/tutorials/using-jsx-with-vue-and-why-you-should-care?utm_campaign=Revue%20newsletter&utm_medium=Newsletter&utm_source=Vue.js%20News)
* [Compound components](https://forum.vuejs.org/t/compound-components/30139)
* [Creating Multi-root Vue.js Components](https://zendev.com/2018/05/07/multi-root-vue-components.html)
* [Understanding Vue.js Reactivity in Depth with Object.defineProperty()](https://www.timo-ernst.net/blog/2017/07/26/understanding-vue-js-reactivity-depth-object-defineproperty/)
* [Templating in Vue: Separation of Concerns or Separation of Technology or something else?](https://medium.com/@s.molinari/templating-separation-of-concerns-or-separation-of-technology-or-something-else-123a3d41f0b4)
* [Stashing Vue components data](https://medium.com/@kelin2025/components-stash-f2e14603a874)
* [Creating Reusable Transitions in Vue](https://vuejsdevelopers.com/2018/02/26/vue-js-reusable-transitions/)
* [vue-advanced-workshop](https://github.com/d-levin/vue-advanced-workshop)
* [Do it with Elegance: How to Create Data-Driven User Interfaces in Vue](https://blog.rangle.io/how-to-create-data-driven-user-interfaces-in-vue/)
* [Creating Vue.js Component Instances Programmatically](https://css-tricks.com/creating-vue-js-component-instances-programmatically/)
* [Managing User Permissions in a Vue.js App](https://dzone.com/articles/managing-user-permissions-in-a-vuejs-app)
* [Render Functional Components in Vue.js](https://alligator.io/vuejs/render-functional-components/)
* [Looping through Object Properties](https://codingexplained.com/coding/front-end/vue-js/looping-object-properties)
* [Cancelling async operations in Vue.js](https://codeburst.io/cancelling-async-operations-in-vue-js-3d0f3c2de598)
* [Scoped styles with v-html](https://medium.com/@brockreece/scoped-styles-with-v-html-c0f6d2dc5d8e)
* [Pagination With Vuejs](https://medium.com/@obapelumi/pagination-with-vuejs-1f505ce8d15b)
* [What does the ‘h’ stand for in Vue’s render method?](https://css-tricks.com/what-does-the-h-stand-for-in-vues-render-method/)
* [How To Build Vue Components That Play Nice](https://vuejsdevelopers.com/2018/06/18/vue-components-play-nicely/)
* [Making responsive Vue components with ResizeObserver](https://itnext.io/making-adaptive-vue-components-with-resizeobserver-123b5ebb20ae)
* [An imperative guide to forms in Vue.js](https://blog.logrocket.com/an-imperative-guide-to-forms-in-vue-js-7536bfa374e0)
* [Vue.js: the good, the meh, and the ugly](https://medium.com/@Pier/vue-js-the-good-the-meh-and-the-ugly-82800bbe6684)
* [Dynamic Vue.js Layout Components](https://markus.oberlehner.net/blog/dynamic-vue-layout-components/)
* [Advanced Vue.js concepts: mixins, custom directives, filters, transitions, and state management](https://blog.logrocket.com/advanced-vue-js-concepts-mixins-custom-directives-filters-transitions-and-state-management-ca6955905156)
* [Introducing the Single Element Pattern](https://medium.freecodecamp.org/introducing-the-single-element-pattern-dfbd2c295c5d)
* [Control DOM Outside Your Vue.js App with portal-vue](https://alligator.io/vuejs/portal-vue/)
* [Add i18n and manage translations of a Vue.js powered website](https://medium.com/hypefactors/add-i18n-and-manage-translations-of-a-vue-js-powered-website-73b4511ca69c)
