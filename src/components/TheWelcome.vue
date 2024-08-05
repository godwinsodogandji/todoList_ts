<script setup lang="ts">
import FormComponent from "./FormComponent.vue";
import TodoList from "./TodoListComponent.vue";
import { nanoid } from "nanoid";
import { ref } from "vue";
import type { Todo } from "../types";
const toDos = ref<Todo[]>([
  { id: nanoid(), text: "courir", isDone: true },
  { id: nanoid(), text: "manger", isDone: true },
  { id: nanoid(), text: "danser", isDone: true },
]);

// function d'ajout 
function getTaskName(taskName: string): void {
  const newTodo: Todo = { id: nanoid(), text: taskName, isDone: false };

  toDos.value.push(newTodo);
}

</script>

<template>
  <div class="flex border boxsizing">
    <h1>Liste de tâches</h1>
    <FormComponent @sendTaskName="getTaskName" />
    <TodoList :getAllTodo="toDos" />
  </div>
</template>

<style scoped>
.flex {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 15px;
}
h1 {
  font-size: 3.5rem;
}
.border {
  border: 5px solid red;
  border-radius: 20px;
}
.boxsizing {
  padding-block: 20px;
  margin: 0 auto;
}
</style>