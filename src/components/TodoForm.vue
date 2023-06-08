<template>
  <form @submit.prevent="addTask">
    <input type="text" v-model="newTask" placeholder="Dodaj nowe zadanie" maxlength="255"/>
    <button type="submit"><i class="fa fa-circle-down"></i></button>
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

<style scoped>
@import '@fortawesome/fontawesome-free/css/all.css';

form {
  position: relative;
}

input {
  width: 50%;
  background-color: #3E3364;
  border-radius: 12px;
  line-height: 40px;
  padding: 0 10px;
  color: white;
  border: 2px solid #1E1A3C;
}

button {
  position: absolute;
  top: 50%;
  right: 15%;
  transform: translateY(-50%);
  font-size: 1.8rem;
  border: none;
  background-color: #1E1A3C;
  cursor: pointer;
  transition: .2s;
  color: white;
}

button:hover {
  transform: translateY(-50%) scale(1.2);
}

</style>
