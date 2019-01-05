<template>
<div>
<todos   @changeStateTask="changeStateTask" @deleteOneTask="deleteOneTask" @addTask="addTask" :store="storeTodo"></todos>

</div >
</template>

<script> 
import Todos from './components/Todos'
import {store} from './store/ListeStore.js'



export default {
  name: 'app',
  store,
  data: function(){
    return{
      storeTodo: store.state.tasks
  }
  },
  components: {
    Todos
  },
  methods : {
    addTask (val) {

      if(val.trim().length > 0){
      store.state.tasks.push({name: val,state: false})
      }

    },
   deleteOneTask (index) {
     this.$delete(store.state.tasks,index)   
  },
  changeStateTask (row) {
     store.state.tasks.forEach(element => {
          if(element.name === row.name)
          {
              if(element.state)
              element.state = false
              else
               element.state = true
          }
     });
  }
  }
}
</script>

