<template>
   <div id="app">
     <todo-app></todo-app>
     <login></login>
   </div>
</template>


<script>
import Login from './components/Login.vue'
import TodoApp from './components/TodoApp.vue'
export default {
   name:'App',
   components:{
      TodoApp,
      Login
      
   }
      
   }

</script>