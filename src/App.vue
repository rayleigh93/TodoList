<template>
<div>
<todos @aFaire="aFaire" @faite="faite" @deleteTacheFinis="deleteTacheFinis"
@checkAllBox="checkAllBox"  @changeStateTask="changeStateTask" @deleteOneTask="deleteOneTask" @addTask="addTask" :store="storeTodo"></todos>

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
      store.state.tasks.push({name: val,state: false,checked: false})
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
  },
  checkAllBox (isCheck){
     this.storeTodo.forEach(element => {
       if(isCheck)
       element.checked = true
       else
       element.checked = false
     });
  },aFaire () {
     this.storeTodo.forEach(element => {
       if(element.checked)
        {
          element.state = false
        }
     });
  },
  faite () {
     this.storeTodo.forEach(element => {
       if(element.checked)
        {
          element.state = true
        }
     });
  },
  deleteTacheFinis() {
      const size = this.storeTodo.length
      for(var index = this.storeTodo.length - 1 ; index >= 0 ; index--){

            if(this.storeTodo[index].state )
            {
                  this.storeTodo.splice(index,1)
            }
            
      }
     
        
       
     

  }

  }
}
</script>

