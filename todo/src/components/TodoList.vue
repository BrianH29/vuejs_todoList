<template>
  <div>
    <ul>
      <li v-for="(todo, index) in propsdata" v-bind:key="todo.item" class="shadow">
        <i class="fas fa-check checkBtn" 
        v-bind:class="{checkBtnCompleted: todo.completed}"
        v-on:click="checkComplete(todo)">
        </i>
        <span v-bind:class="{checkBtnCompleted:todo.completed}">{{ todo.item }}</span>
        <span class="removeBtn" v-on:click="removeTodo(todo,index)">
          <i class="fas fa-trash-alt"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['propsdata'],
  methods:{
    removeTodo : function(todo, index){
      this.$emit('removeTodo',todo, index); 
    },
    checkComplete: function(todo){
      todo.completed = !todo.completed; 
      localStorage.removeItem(todo.item);
      localStorage.setItem(todo.item, JSON.stringify(todo));
    }
  }

}
</script>

<style scoped>
  ul{
    list-style: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }
  li{
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height:50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }
  .removeBtn{
    margin-left: auto;
    color: #de4343;
  }
  .checkBtn{
    line-height: 45px;
    color: #18b940;
    margin-right: 5px;
  }
  .checkBtnCompleted{
    color:#b3adad;
  }
  .textCompleted{
    text-decoration: line-through;
    color:#b3adad;
  }

</style>