<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodo" v-on:keyup.enter="addTodo">
    <span class="addContainer" @click="addTodo">
      <i class="far fa-calendar-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data : function(){
    return {
      newTodo: ""
    }
  },
  methods : {
    addTodo : function(){
      //빈 값 입력 방지
      if(this.newTodo !== ''){
        this.$emit('addTodo',this.newTodo);
        this.clearInput(); 
      }
    },
    clearInput: function(){
      this.newTodo = ''; 
    }
  }

}
</script>

<style scoped>
input:focus{
  outline:none;
}
.inputBox{
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input{
  border-style: none;
  font-size: 0.9rem;
}
.addContainer{
  float: right;
  background: linear-gradient(to right, #18b940, #4fe23b);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
  size: 2rem;
}
.closeModalBtn {
  color: #42b983;
}
</style>