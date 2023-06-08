<template>
  <form @submit.prevent="addTask">
    <input type="text" v-model="newTask" placeholder="Dodaj nowe zadanie" />
    <button type="submit">Dodaj</button>
  </form>
</template>

<script>
import { ref } from 'vue';

export default {
  emits: ['add-task'],

  setup(props, {emit}) {
    const newTask = ref('');

    const addTask = () => {
      if (newTask.value.trim() !== '') {
        emit('add-task', newTask.value);
        newTask.value = '';
      }
    };

    return {
      newTask,
      addTask,
    };
  },
};
</script>
