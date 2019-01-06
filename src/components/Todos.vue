<template>
<div>    


<el-container style="width: 1000px">
  <el-container>
    <el-header>
      <p class = "taskStyleHeader" >Todo List</p>
    </el-header>




    <el-main>
      <todos-body 
       @checkAllBox="checkAllBox" @changeStateTask="changeStateTask" @deleteOneTask="deleteOneTask" @addTask="addTask" :store="store"></todos-body>
    </el-main>


    <el-footer>
      <todos-footer @aFaire="aFaire" @faite="faite" @deleteTacheFinis="deleteTacheFinis" :store="store"></todos-footer>
    </el-footer>


  </el-container>
</el-container>




</div>    
</template>



<script>

import todosBody from './TodosBody.vue'
import todosFooter from './TodosFooter.vue'

export default {
    name:'todos',
    props: ['store'] ,
    components: {
      todosBody,
      todosFooter
    },
   data: function () {
  return {
    
  }
},
methods: 
{
  addTask (val) {
        this.$emit("addTask",val)
  },
   deleteOneTask (index) {
        this.$emit("deleteOneTask",index)
  },
  changeStateTask (row) {
      this.$emit('changeStateTask',row)
  },
  checkAllBox (isCheck){
     this.$emit('checkAllBox',isCheck)
  },
  aFaire () {
      this.$emit('aFaire')
  },
  faite () {
      this.$emit('faite')
  },
  deleteTacheFinis() {
      this.$emit('deleteTacheFinis')
  }

}
}
</script>




<style>
.taskStyleHeader{
  font-family: "Helvetica Neue";
  font-size: 30px;
  text-align: center;
  font-weight:bold;
}
</style>
