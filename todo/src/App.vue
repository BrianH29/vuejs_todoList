<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInsert v-on:addTodo="addTodoItem"></TodoInsert>
    <TodoList v-bind:propsdata="todoList" v-on:removeTodo="removeTodo"></TodoList>
    <TodoFooter></TodoFooter>

  </div>
</template>

<script>
import TodoHeader from './components/Header.vue'
import TodoInsert from './components/insertTodo.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/Footer.vue'

export default {
  data: function(){
    return {
      todoList: [],
    }
  },
  methods:{
    addTodoItem : function(todo){
      var obj = {completed:false, item: todo};
      localStorage.setItem(todo, JSON.stringify(obj));
      this.todoList.push(obj); 
    },
    removeTodo : function(todo, index){
      localStorage.removeItem(todo);
      this.todoList.splice(index,1);
    }
  },
  created: function() {
    if(localStorage.length > 0){
      for(let i = 0; i<localStorage.length; i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoList.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
  },
  components : {
    'TodoHeader':TodoHeader,
    'TodoInsert':TodoInsert,
    'TodoList' : TodoList,
    'TodoFooter': TodoFooter
  }
}
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f6;
}
input{
  border-style: groove;
  width: 200px;
}
button {
  border-style : groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
