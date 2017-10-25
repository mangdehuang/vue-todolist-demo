<template>
  <div class="TodoItem">
    <el-row>
      <el-col :span="24" class="todo-item">
        <div class="grid-content bg-purple-dark height100">
          <!--<el-col :span="1" class="height100">
            <el-radio class="radio left radio-pos" v-model="radio" label="1"></el-radio>
          </el-col>
          <el-col class="todo-content height100" :span="21">11</el-col>
          <el-col :span="2" class="todo-time height100">11</el-col>-->

          <el-col :span="20" class="height100 todo-content">
            <el-radio class="radio left radio-pos" v-model="radio" label="1">
              <span>{{content}}</span>
            </el-radio>
          </el-col>
          <el-col :span="4" class="todo-time height100">{{createDate}}</el-col>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  data () {
    return {
      radio:'1',
      content:'',
      createDate:''
    }
  },
  props:{
    todoItem:{}
  },
  mounted(){
      let _this = this;
      this.$nextTick(() => {
        _this.radio = _this.todoItem.done;
        _this.content = _this.todoItem.content;
        _this.createDate =_this.todoItem.date;
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .radio-pos{
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
</style>
