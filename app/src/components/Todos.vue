<template>
  <div class="todos-holder">
    <input type="text" placeholder="enter your todo" v-model="currentTodo" @keyup.enter="addTodo"/>
    <div v-for="(todo,index) in todos" :key="todo.id" class="todo-box">
        <div>{{todo.message}}</div>
        <button @click="removeTodo(index)">X</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todos",
  data() {
    return {
      currentTodo: "",
      newId: 3,
      todos: [
        {
          id: 1,
          message: "finish homework",
          completed: false,
        },
        {
          id: 2,
          message: "eat some food",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.currentTodo.trim() == 0) {
        return;
      }
      this.todos.push({
        id: this.newId,
        message: this.currentTodo,
        completed: false,
      })

      this.currentTodo = '';
      this.newId++;
    },
    removeTodo(id) {
      this.todos.splice(id, 1);
      this.newId--;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todos-holder {
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content:center;
}
.todos-holder input {
  width: 90%;
  padding: 10px 10px;
  font-size: 18px;
  margin-bottom: 16px;
}
.todo-box {
  display: flex;
  justify-content: space-between;
  width: 90%;
  margin: 10px;
  border: solid black;
  padding: 20px;
}
.todo-box:hover {
  transition:transform 0.1s;
  transform: scale(1.025);
}
</style>
