# vue-todolist-demo

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

```
### 注意
在v-for中指定key
```
<component v-for="(item,index) in arr" :key="index"></component>
不指定key时  会发生渲染错误  但是在官网的介绍中说不会出错
component lists rendered with v-for should have explicit keys. See https://vuejs.org/guide/list.html#key for more info. 
(found in <Root>)
```
