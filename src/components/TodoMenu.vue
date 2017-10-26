<template>
  <div class="TodoMenu">
    <el-row>
      <el-col :span="24">
        <div class="grid-content bg-purple-dark height100">
          <el-select v-model="selectValue" class="left small" @change="changeOption">
            <el-option v-for="item in selectOptions"
                       :key = "item.key"
                       :label = "item.label"
                       :value = "item.value"
                       placeholder="请选择"></el-option>
          </el-select>
          <i class="el-icon-plus right add-icon" @click="showInput"></i>
        </div>
      </el-col>
    </el-row>
    <el-row v-if="inputShow" class="todo-input">
      <el-col :span="24">
        <el-input  v-model="content" placeholder="请输入内容"></el-input>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'TodoMenu',
  data () {
    return {
      inputShow:false,
      selectValue:'0',
      content:'',
      selectOptions:[
        {
          value:'0',
          label:'未完成',
        },
        {
            value:'1',
           label:'已完成'
        },
        {
          value:'2',
          label:'全部'
        }
      ],
    }
  },
  methods:{
    showInput (){
        this.inputShow = !this.inputShow;
    },
    changeOption (){
        this.$emit("changeOption",this.selectValue+"");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .bg-purple-dark {
    background: #D6F4FE;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .small{
    width: 95px;
  }
  .add-icon{
    margin: 10px 10px 0 0 ;
    color: #819298;
  }
  .add-icon:hover{
    cursor: pointer;
  }
  .TodoMenu{
    position: relative;
  }
  .todo-input{
    position: absolute;
    z-index: 2;
    width: 100%;
  }
</style>
