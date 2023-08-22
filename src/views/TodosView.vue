<script setup>
import { ref } from "vue";
// import { uid } from 'uid';
import TodosList from '../components/TodosList.vue'
import TodoCreator from '../components/TodoCreator.vue';

const todoContent = ref([]);
let isListEmpty = true;
const creatTodo = (name, email, time) => {
  todoContent.value.push({
    // id: uid(),
    // id: counter++,
    tname: name,
    tmail: email,
    ttime: time,
    isCompleted: false,
  })
  isListEmpty = false;
}

const toggleCompleteTodos = (ind) => {
  todoContent.value[ind].isCompleted = !todoContent.value[ind].isCompleted;
}
</script>

<template>
  <main class="container text-center mt-5">
    <h1>Create New Todo</h1>
    <p>Initialize Your New Task</p>

    <TodoCreator @create-todo="creatTodo" />

    <p v-show="isListEmpty" class="mt-3"> 📄 You have no Todo's to complete!! Create One! ✏ </p>
    <table v-show="!isListEmpty" class="table table-bordered border-dark bg-light mt-3">
      <thead>
        <tr>
          <th scope="col">Completed</th>
          <th scope="col">Task Name</th>
          <th scope="col">Tasker Email</th>
          <th scope="col">Task Time</th>
        </tr>
      </thead>
      <tbody>
        <TodosList v-for="(todo, index) in todoContent" :todo="todo" :index="index"
          @toggle-complete="toggleCompleteTodos" />
      </tbody>
    </table>

  </main>
</template>
