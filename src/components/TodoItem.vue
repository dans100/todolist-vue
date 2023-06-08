<template>
  <li>
    <span :class="{ 'completed-task': status }">{{ task.title }}</span>
    <button @click="deleteTask">Usuń</button>
    <button @click="toggleStatus">Zmień status</button>
  </li>
</template>

<script>

export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
    status: {
      type: Boolean,
      required: true,
    },
  },

  setup(props, { emit }) {

    const deleteTask = () => {
      emit('delete-task', props.index);
    };

    const toggleStatus = () => {
      emit('toggle-status', props.index);
    };

    return {
      deleteTask,
      toggleStatus,
    };
  },
};
</script>

<style scoped>

li {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}

.completed-task {
  text-decoration: line-through;
}

</style>
