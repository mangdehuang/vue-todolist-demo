# vue-todolist-demo

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

```
## todolist的基本实现

筛选完成 未完成 全部

添加一个todoitem

修改已做/未做状态

删除某一条记录

## 控件
element-ui
vue-resource

### 注意
在v-for中指定key
```
<component v-for="(item,index) in arr" :key="index"></component>
不指定key时  会发生渲染错误  但是在官网的介绍中说不会出错
component lists rendered with v-for should have explicit keys. See https://vuejs.org/guide/list.html#key for more info. 
(found in <Root>)
```
- 数组的查找中不用index 作为key 使用date为key 进行查找删除
- 如果父组件给子组件的是数组或者对象  修改子组件会同时修改父组件
- 官方不建议使用子组件直接修改父组件  用$emit 最好
