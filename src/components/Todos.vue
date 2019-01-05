<template>
<div>    


<el-container style="width: 500px">
  <el-container>
    <el-header>
      <p>Todo List</p>
    </el-header>




    <el-main>
      <todos-body @changeStateTask="changeStateTask" @deleteOneTask="deleteOneTask" @addTask="addTask" :store="store"></todos-body>
    </el-main>


    <el-footer>Footer</el-footer>
  </el-container>
</el-container>




</div>    
</template>



<script>

import todosBody from './TodosBody.vue'

export default {
    name:'todos',
    props: ['store'] ,
    components: {
      todosBody
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
  }

}
}
</script>
