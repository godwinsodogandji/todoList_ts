<template>
  <div class="container">
    <ul>
      <li v-for="(todo, index) in getAllTodo" :key="index">
        <input type="checkbox" class="form-check-input" />
        <label for="text" class="form-check-label"> {{ todo.text }}</label>
        <span>{{ todo.isDone ? " Traitée" : " Non traitée" }}</span>
        <span class="mod"><button @click="modifierTexte(index)">🔍</button></span>
        <span class="sup" @click="remove(index)"> X</span>
       
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import type { Todo } from "../types";
const props = defineProps<{
  getAllTodo: Todo[];
}>();
console.log(props.getAllTodo);
//  fonction de modification

const modifierTexte = (index: number): void => {
  const tacheModifier = props.getAllTodo[index];
  const nouvelleDescription: string | null = prompt(
    "Entrez la nouvelle description de la tâche :"
  );
  if (nouvelleDescription) {
    tacheModifier.text = nouvelleDescription;
  }
};
// fonction de suppression

function remove(index: number): void {
  props.getAllTodo.splice(index, 1);
}
</script>

<style scoped>
li {
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  font-size: 1.5rem;
  color: rgb(30, 144, 255);
  list-style: none;
}
.container {
  border: solid 2px;
  border-radius: 1rem;
  padding: 5em;
}
.sup {
  padding: 1px;
  border: 1px;
  cursor: pointer;
  color: white;
  background-color: red;
  border-radius: 5rem;
}
.mod {
    padding: 2px;
}
</style>