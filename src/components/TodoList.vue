<template>
  <TodoHeader />
  <div>
    <TodoForm @add-task="handleAddTask" />
    <ul v-if="tasks.length > 0">
      <TodoItem
          v-for="(task, index) in tasks"
          :key="index"
          :task="task"
          :index="index"
          :status="task.status"
          @delete-task="deleteTask"
          @toggle-status="toggleTaskStatus"
      />
    </ul>
    <p v-else>Lista zadań jest pusta</p>
  </div>
</template>

<script>
import { ref } from 'vue';
import TodoHeader from "@/components/TodoHeader";
import TodoForm from "@/components/TodoForm";
import TodoItem from "@/components/TodoItem";

export default {
  name: 'TodoList',
  components: { TodoItem, TodoForm, TodoHeader },
  setup() {
    const tasks = ref([]);

    const handleAddTask = (newTask) => {
      tasks.value.push({ title: newTask, status: false });
    };

    const deleteTask = (index) => {
      tasks.value.splice(index, 1);
    };

    const toggleTaskStatus = (index) => {
      tasks.value[index].status = !tasks.value[index].status;
    };

    return {
      tasks,
      handleAddTask,
      deleteTask,
      toggleTaskStatus,
    };
  },
};
</script>

<style scoped>

div {
  margin: 10vh auto;
  width: 80%;
  max-width: 800px;
  box-shadow: 0 1px 8px black;
  background-color: #1E1A3C;
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: center;
  color: #fff;
  padding: 20px 10px;
  opacity: 75%;
  animation: slide-down 300ms ease-out forwards;
}

ul {
  list-style: none;
  padding: 0;
}

@keyframes slide-down {
  from {
    opacity: 0;
  }
  to {
    opacity: 75%;
  }
}

</style>
