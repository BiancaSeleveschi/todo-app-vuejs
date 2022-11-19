<template>
  <div id="app">
    <!--    <img alt="Vue logo" src="./assets/logo.png">-->
    <div class="container">
      <p>Lista de lucruri de facut pentru azi</p>
      <i class="fa fa-bookmark color-rgb"></i>
      <div class="input-group mb-3">
        <input type="text" class="form-control" id="add-input" placeholder="To do" aria-label="Recipient's username"
               v-model="todo.name"
               aria-describedby="button-addon2">
        <button class="btn btn-primary" @click="addNewTodo" id="add-button" type="button">Add</button>
      </div>
      <div class="row justify-content-between">
        <div class="col" id="list-group1-id ">
          <h2>To do items</h2>
          <ul class="list-group" id="list-group-id">
            <li v-for="(todo, index) in toDoList" v-bind:key="index"
                class="list-group-item my-3 border border-2 rounded border-primary d-flex justify-content-between">
              <div>{{ todo.name }} -- index: {{ index }}</div>
              <div>
                <button class="btn"><i class="bi bi-bookmark"></i></button>
                <!--                <button :class="[todo.isDone ? 'btn btn-success' : 'btn btn-primary']" @click="markDoneTodo(index)">-->
                <button class="btn" :class="[todo.isDone ? 'btn-success' : 'btn-primary']" @click="markDoneTodo(index)">
                  {{ todo.isDone ? "Undone" : "Done" }}
                </button>
                <button class="btn btn-danger">Delete</button>
              </div>
            </li>
          </ul>
        </div>
        <div class="col" id="list-group2-id ">
          <h2 id="done-items-id">Done items</h2>
          <ul class="list-group2" id="list-group2-id">
          </ul>
        </div>
      </div>
      <div>
        <h2 id="important-items-id">Important items</h2>
        <ul class="list-group3" id="list-group3-id">
        </ul>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      toDoList: [
        {
          id: 1,
          name: "Citesc 25 de pagini",
          isDone: false,
          isImportant: false,
        },
        {
          id: 2,
          name: "Sport 30 minute",
          isDone: false,
          isImportant: false,
        },
        {
          id: 3,
          name: "Beau 3 litri de apa",
          isDone: false,
          isImportant: true,
        }
      ],
      todo: {name: "", isDone: false, isImportant: false, id: ""}
    }
  },
  methods: {
    addNewTodo() {
      this.toDoList.push(this.todo)
    },
    markDoneTodo(index) {
      console.log(this.toDoList)
      //modificam isDone cu inverul lui
      //daca isDone ii true atunci afisam butonul cu textul "Undone"  si culoarea verde daca e false afisanm "Done si culoarea de bg albastra

      this.toDoList[index].isDone = !this.toDoList[index].isDone;

      console.log("todo")
      console.log(this.toDoList[index])
      console.log(index)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
