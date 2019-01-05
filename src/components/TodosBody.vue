<template>
<div>
<el-row>

      <el-col>
      <el-input placeholder="Please input" v-model="input" @keyup.enter.native="addTask" ></el-input>
      <el-button type="primary" plain @click="addTask">Ajouter la tâche</el-button>
      </el-col>

      <el-col>
        
      <el-table
            ref="multipleTable"
            :data="store"
            style="width: 100%"
            @row-click="changeStateTask">


              <el-table-column width="380px"  >
                <template slot-scope="scope"  >

                    <p v-if="scope.row.state"> <s>{{scope.row.name}}</s></p>
                    <p v-if="!scope.row.state"> {{scope.row.name}}</p>

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
    input: ""
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
  }

}
}
</script>
