<template>
  <div class="TodoItem">
    <el-row>
      <el-col :span="24" class="todo-item">
        <div class="grid-content bg-purple-dark height100">
          <el-col :span="12" class="height100 todo-content">
            <div class="left msg-pos">
              <span>{{this.todoItem.content}}</span>
            </div>
          </el-col>
          <el-col :span="3" class="height100"><i class="state-icon base-icon" :class="doneClass" @click="changeState"></i></el-col>
          <el-col :span="6" class="todo-time height100 red state-icon">{{createDate}}</el-col>
          <el-col :span="3" class="height100"><i class="el-icon-circle-close state-icon base-icon" @click="delItem"></i></el-col>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  import util from '../components/util'

export default {
  name: 'TodoItem',
  data () {
    return {
    }
  },
  props:{
    todoItem:{},
  },
  computed:{
    doneClass(){
      return parseInt(this.todoItem.done) ? 'el-icon-star-on':'el-icon-star-off';
    },
    createDate(){
      return util.getMMDDHHmmbyMil(this.todoItem.date);;
    }
  },
  methods:{
    changeState(event){
//      if (event) {
//        console.log(event.target.tagName)
//      }
      this.todoItem.done = util.change01(this.todoItem.done)+'';
    },
    delItem (){
        this.$emit('delItem',this.todoItem);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .msg-pos{
    margin:5px 0 0 5px;
  }
  .todo-content{
    /*background-color: rosybrown;*/
  }
  .todo-time{
    /*background-color: aqua;*/
  }
  .todo-item{
    height: 30px;
  }
  .TodoItem{
    border-bottom: 1px dashed #d9d9d9;
  }
  .TodoItem:hover{
    background-color: #e7e7e7;
  }
  .center{
    margin: 0 auto;
  }
  .state-icon{
    position: relative;
    top:13%;
  }
</style>
