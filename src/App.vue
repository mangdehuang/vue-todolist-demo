<template>
  <div id="app">
    <p>TodoList</p>
    <TodoMenu @changeOption="changeType"></TodoMenu>
    <div>
      <TodoItem  v-for="(item,index) in todoThings"
                 v-if="(showDown == item.done)||(showDown =='2')"
                 :todoItem="item"
                 :key="index">

      </TodoItem>
    </div>
  </div>
</template>

<script>
import TodoMenu from './components/TodoMenu'
import TodoItem from './components/TodoItem'

export default {
  name: 'app',
  components: {
    HelloWorld,
    TodoMenu,
    TodoItem
  },
  data () {
      return {
          showDown:'0',
          todoThings:[]
      }
  },
  mounted () {
      let _this = this;
      this.$nextTick(() => {
        _this.getData();
      });
  },
  methods:{
      getData (){
        this.$http.get('./static/data/data.json').then(res => {
            this.todoThings = res.body.data;
            console.log(this.todoThings);
        });
    },
    changeType (type){
        this.showDown = type;
        console.log(type);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin-left: 60px;
  width: 500px;
  height: 300px;
  border: 1px solid rosybrown;
}
  .left{
    float: left;
  }
  .right{
    float: right;
  }
  .height100{
    height: 100%;
  }
</style>
