<template>
  <div>
    <section>
      <ul>
        <li v-for="(todoItem, index) in todoItems" class="shadow">
<!--          <input type="checkbox">-->
          <i class="fa fa-check checkBtn" aria-hidden="true"></i>
          {{todoItem}}
          <span class="removeBtn">
            <i class="fa fa-trash-o removeBtn" aria-hidden="true" @click="removeTodo(todoItem, index)"></i>
          </span>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data(){
    return {
      todoItems: []
    }
  },
  methods:{
    removeTodo(key,idx){
      localStorage.removeItem(key);
      this.todoItems.slice(idx, 1);
      debugger;
    }
  },
  created() {
    if(localStorage.length){
      for (let i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  }

}
</script>

<style scoped>
ul{
  list-style-type: none;
  text-align: left;
  padding: 0px;
}
li{
  display: flex;
  min-height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  border-radius: 5px;
  background: white;
}
.checkBtn{
  line-height: 45px;
  color: darkolivegreen;
  margin-left: 5px;
  margin-right: 10px;
}
.removeBtn{
  margin-left: auto;
  color: tomato;
}
</style>
