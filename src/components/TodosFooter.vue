<template>
    <div>

<el-row :gutter="5">
  <el-col :span="5">
      <p class="taskStyleFooter"> <strong>{{store.length}} tâches </strong> à faire</p>
  </el-col>
  <el-col :span="5">
        <el-button type="primary" @click.native="aFaire"  plain>A Faire</el-button>
  </el-col>
   <el-col :span="5">
       <el-button type="success"  @click.native="faite" plain>Faite</el-button>
  </el-col>
  
   <el-col :span="5">
       <el-button type="danger" @click.native="deleteTacheFinis" splain>Supprimer les tâches finies</el-button>
  </el-col>
   
</el-row>


    </div>
</template>



<script>

export default {
    name:"todosFooter",
    props: ['store'] ,
   data: function () {
  return {
    
  }
},
methods: 
{
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
.taskStyleFooter{
  font-family: "Helvetica Neue";
  font-size: 15px;
}
</style>