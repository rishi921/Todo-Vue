<template>
    <div class="container-fluid p-4">
      <!-- Heading -->
      <div class="row">
        <div class="col font-weight-bold">Task</div>
        <div class="col-2 font-weight-bold">Done</div>
        <div class="col-2 font-weight-bold">Actions</div> <!-- New Column for Actions -->
      </div>
  
      <!-- List item -->
      <div class="row" v-for="(t, index) in filteredTasks" :key="t.action">
        <div class="col">{{ t.action }}</div>
        <div class="col-2">
          <input type="checkbox" v-model="t.done" class="form-check-input" />
        </div>
        <div class="col-2">
          <button class="btn btn-danger btn-sm" @click="deleteTask(index)">Delete</button>
        </div>
      </div>
  
      <!-- Hiding -->
      <div class="row bg-secondary py-2 mt-2 text-white">
        <div class="col text-center">
          <input
            type="checkbox"
            v-model="hideCompleted"
            class="form-check-input"
          />
          <label class="form-check-label font-weight-bold">
            Hide Completed Tasks
          </label>
        </div>
      </div>
  
      <!-- Input Box -->
      <div class="row py-2">
        <div class="col">
          <input v-model="newItemText" class="form-control" />
        </div>
  
        <div class="col-2">
          <button class="btn btn-primary p-2" @click="addNewTodo">
            Add
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "Todo",
    data() {
      return {
        tasks: [],
        hideCompleted: false,
        newItemText: ''
      };
    },
    computed: {
      filteredTasks() {
        return this.hideCompleted
          ? this.tasks.filter((t) => !t.done)
          : this.tasks;
      },
    },
    methods: {
      addNewTodo() {
        if (this.newItemText.trim()) {
          this.tasks.push({
            action: this.newItemText,
            done: false,
          });
          localStorage.setItem('todos', JSON.stringify(this.tasks));
          this.newItemText = "";
        }
      },
      deleteTask(index) {
        this.tasks.splice(index, 1);
        localStorage.setItem('todos', JSON.stringify(this.tasks));
      }
    },
    created() {
      let data = localStorage.getItem('todos');
      if (data) {
        this.tasks = JSON.parse(data);
      }
    }
  }
  </script>
  
  <style>
  .container-fluid {
    max-width: 600px;
    margin: auto;
  }
  
  .my-2 {
    margin-top: 10px;
    margin-bottom: 10px;
  }
  </style>