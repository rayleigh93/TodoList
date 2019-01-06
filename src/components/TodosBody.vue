<template>
<div>
<el-row>

      <el-col >
    
          <el-row>
            <el-col :span="2">      
           <el-checkbox v-model="checkAll"  @change="checkAllBox"></el-checkbox> 
            </el-col>
            <el-col :span="100">   
         <el-input placeholder="Please input" v-model="input" @keyup.enter.native="addTask" ></el-input>
            </el-col>
          </el-row>

         <el-button type="primary" plain @click="addTask">Ajouter la tâche</el-button>
         
      </el-col>
      


      <el-col >
       <el-table
            ref="multipleTable"
            :data="store"
            style="width: 100%"
            @row-click="changeStateTask"
            empty-text="Vous n'avez aucune tâches à faire actuellement">

            <el-table-column>
              <template slot-scope="scope">
                 <el-checkbox @change="checkBox" v-model="scope.row.checked"></el-checkbox>
              </template>           
            </el-table-column>


            <el-table-column width="500px">
              <template slot-scope="scope">
                    <p  class="taskStyle" v-if="scope.row.state"> <s>{{scope.row.name}}</s></p>
                    <p  class="taskStyle" v-if="!scope.row.state"> {{scope.row.name}}</p>
              </template>
            </el-table-column>
        

            <el-table-column>
              <template slot-scope="scope">
                <el-button type="danger" icon="el-icon-delete" @click.stop="$emit('deleteOneTask',scope.$index)" circle></el-button>
              </template>
            </el-table-column>



          </el-table>
        </el-col>



</el-row>
</div>    
</template>



<script>

export default {
    name:"todosBody",
    props: ['store'] ,
   data: function () {
  return {
    input: "",
    checkAll: false
  }
},
methods: 
{
  addTask (val) {
      this.$emit('addTask',this.input)
      this.input = ""
  },
  changeStateTask (row, event, column) {
     
      this.$emit('changeStateTask',row)
  },
  checkAllBox (){
     this.$emit('checkAllBox',this.checkAll)
  },
  checkBox (){
     this.checkAll = false
  }

}
}
</script>


<style>
.taskStyle{
  font-family: "Helvetica Neue";
  font-size: 20px;
}
</style>
