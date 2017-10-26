<template>
  <div class="TodoItem">
    <el-row>
      <el-col :span="24" class="todo-item">
        <div class="grid-content bg-purple-dark height100">
          <el-col :span="14" class="height100 todo-content">
            <div class="left msg-pos">
              <span>{{content}}</span>
            </div>
          </el-col>
          <el-col :span="4" class="height100"><i class="state-icon base-icon" :class="doneClass" @click="changeState"></i></el-col>
          <el-col :span="6" class="todo-time height100">{{createDate}}</el-col>
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
      done:'0',
      content:'',
      createDate:'',
    }
  },
  props:{
    todoItem:{},
    todoIndex:{}
  },
  mounted(){
      let _this = this;
      this.$nextTick(() => {
        _this.done = _this.todoItem.done;
        _this.content = _this.todoItem.content;
        _this.createDate = util.getMMDDHHmmbyMil(_this.todoItem.date);
        _this.todoItem.index = _this.todoIndex;
      });
  },
  computed:{
    doneClass(){
      return parseInt(this.done) ? 'el-icon-star-on':'el-icon-star-off';
    }
  },
  methods:{
    changeState (event){
//      if (event) {
//        console.log(event.target.tagName)
//      }
      this.done = '1';
      this.$emit("changeState",this.todoItem);
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
