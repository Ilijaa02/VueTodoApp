<template>
  <div id="app">
    <div class="container-fluid">
      <div class="text-center todo">
        <h1 class="text-white pt-5 header-text">TO-DO LIST</h1>
        <div class="header bg-white my-3">
          <input class="input" placeholder="Add new item" v-model="newToDo" />
          <button class="add" @click="add()">Add</button>
        </div>
        <div class="content">
          <ul style="list-style-type: none">
            <li
              v-for="(todo, i) in existingToDo"
              :key="todo"
              class="text-black todo-item"
            >
              <span class="list-text"> {{ todo.text }} </span>
              <button
                class="btn-delete btn-outline-primary"
                @click="deleteToDo(i)"
              >
                X
              </button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      newToDo: "",
      existingToDo: [
        { text: "Go to store", id: 0 },
        { text: "Walk dog", id: 1 },
        { text: "Go to gym", id: 2 },
      ],
    };
  },
  methods: {
    add() {
      this.existingToDo.push({
        text: this.newToDo,
      }),
        (this.newToDo = "");
    },
    deleteToDo(i) {
      this.existingToDo.splice(i, 1);
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-image: linear-gradient(#f12711, #f5af19);
  min-height: 100vh;
}
@media screen and (max-width: 450px){
  .todo{
    width: 100%;
  }
  .input{
    font-size: 20px !important;
    max-width: 200px;
  }
  .header-text{
    font-size: 23px;
  }
  .add{
    font-size: 20px !important;
    width: 30% !important;
  }
  .list-text{
    font-size: 20px;
  }
  .btn-delete{
    float: right !important;
  }
  li{
    width: 100% !important;
  }
}
@media screen and (min-width: 450px){
  .todo{
    max-width: 500px;
  }
}
.todo {
  margin: 0 auto;
}
.header {
  display: flex;
  justify-content: space-between;
  height: 50px;
  border-radius: 10px 10px 0 0;
}
.add {
  border: none;
  background-color: transparent;
  width: 120px;
  font-size: 25px;
  color: blue;
}
.input {
  border: none;
  font-size: 25px;
  padding-left: 25px;
  border-radius: 10px;
}
li {
  position: relative;
  left: -32px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 25px;
  font-size: 23px;
}
.content {
  background-color: white;
  padding-bottom: 1px;
  padding-top: 20px;
  border-radius: 0 0 10px 10px;
}
.todo-item {
  height: 45px;
}
.btn-delete {
  width: 40px;
}
</style>
