<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInsert></TodoInsert>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>

  </div>
</template>

<script>
import TodoHeader from './components/Header.vue'
import TodoInsert from './components/insertTodo.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/Footer.vue'

export default {
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
