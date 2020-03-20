# Vue-with-TypeScript



## Table of Contents

1. [Setting](#Setting)
1. [Divide App.vue file](#Divide-App.vue-file)
1. [컴포넌트 등록](#컴포넌트-등록)
1. 
1. 

---



## Setting



## Divide App.vue file

분리해서 개발하면 코드의 가독성과 협업성이 높아지게 되고, IDE의 지원도 향상됨. 다만 관리해야 하는 파일이 많아지는 단점이 생긴다.

### 1. 파일 분리를 위해 vue-template-loader  설치

```bash
npm install --save-dev vue-template-loader
```

### 2. vue.config.js 작성

```javascript
module.exports = {
  configureWebpack: {
    module: {
      rules: [
        {
          test: /.html$/,
          loader: "vue-template-loader",
          exclude: /index.html/
        }
      ]
    }
  }
};
```

### 3. src폴더에 shims-html.d.ts 작성

`shims-html.d.ts`는 `html` 파일을 템플릿 형태로 인식하도록 도움

```typescript
declare module '*.html' {
  import Vue, { ComponentOptions, FunctionalComponentOptions } from 'vue';
  interface WithRender {
    <V extends Vue, U extends ComponentOptions<V> | FunctionalComponentOptions>(
      options: U,
    ): U;
    <V extends typeof Vue>(component: V): V;    
  }
  const withRender: WithRender;
  export default withRender;
}
```

### 4. 그리고 각각 파일 나누어서 작성하기



## 컴포넌트 등록

```typescript
import UserInfo from '@/components/UserInfo.vue'; // 절대경로

@Component({
	components: {
		UserInfo,
	}
})
```



## Props

```vue
<template>
  <div>
    {{ name }} > <br/>
    <b>{{ userName }}</b>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component({
  props: {
    name: String,
  },
})

export default class PropsSample extends Vue {
  get userName() {
    return this.$props.name;
  }
}
</script>


```

