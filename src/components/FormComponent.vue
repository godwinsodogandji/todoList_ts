<template>
  <input
    type="text"
    v-model="nouvelleTache"
    placeholder="Ajouter une tâche "
    @keydown.enter="submitTask"
  />
</template>

<script setup lang="ts">
import { ref } from "vue";
const nouvelleTache = ref<string>("");

const emit = defineEmits<{
  (e: "sendTaskName", value: string): void;
}>();

function submitTask(e: Event): void {
  if (nouvelleTache.value.trim() !== "") {
    emit("sendTaskName", nouvelleTache.value);
    nouvelleTache.value = "";
  }


}
</script>

<style scoped>
input {
  padding: 10px;
  font-size: 1.5rem;
  /* margin:auto; */
  /* height: 2rem;
    width: 30rem;; */
}
</style>