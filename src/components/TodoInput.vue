<template>
  <div class="inputBox shadow" >
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" placeholder="Type todo you want to add.">
<!--    <button v-on:click="addTodo">-->
<!--      add-->
<!--    </button>-->
    <span class="addContainer"  v-on:click="addTodo">
      <i class="addBtn fa fa-plus" aria-hidden="true"></i>
    </span>

  </div>
</template>

<script>
export default {
  name: "TodoInput",
  data(){
    return {
      newTodoItem: ''
    }
  },
  methods: {
    addTodo(){
      if(this.newTodoItem.trim()){
        console.log(this);
        debugger;
        let val = this.newTodoItem && this.newTodoItem.trim();
        localStorage.setItem(val, val);
        this.clearInput();
      }
    },
    clearInput(){
      this.newTodoItem = null;
    }

  }
}
</script>

<style scoped>
input:focus{
  outline: none;
}
.inputBox{
  display: flex;
  background: white;
  line-height: 50px;
  height: 50px;
  border-radius: 5px;
}
.inputBox input{
  /*width: available;*/
  width: -webkit-fill-available;
  width: -moz-available;
  border-style: none;
  font-size: 0.8rem;
  border-radius: 5px;
  margin: 0px 20px;
}
.addContainer{
  /*float: right;*/
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: inline-block;
  border-radius: 0 5px 5px 0;
  width: 3rem;
}
.addBtn{
  color: wheat;
  vert-align: middle;
}
</style>
