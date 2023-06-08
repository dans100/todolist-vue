<template>
  <div>
    <TodoHeader />
    <TodoForm @add-task="handleAddTask" />
    <ul>
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

ul {
  list-style: none;
}

</style>
