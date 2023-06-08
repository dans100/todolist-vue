<template>
  <li>
    <span :class="{ 'completed-task': status }">{{ task.title }}</span>
    <button class="trash" @click="deleteTask"><i class="fa fa-trash"></i></button>
    <button :class="['check', {'completed-check': status}]" @click="toggleStatus"><i class="fa fa-circle-check"></i></button>
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
@import '@fortawesome/fontawesome-free/css/all.css';

li {
  position: relative;
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
  width: 100%;
}

span {
  display: inline-block;
  margin: 0 auto;
  overflow: hidden;
  width: 50%;
  background-color: #3E3364;
  border-radius: 12px;
  line-height: 40px;
  color: white;
  border: 2px solid #1E1A3C;
  word-break: break-word;
}

.completed-task {
  text-decoration: line-through;
  background-color: green;
}

button {
  position: absolute;
  top: 50%;
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

.trash {
 right: 15%;
}

.check {
  right: 10%;
}

.completed-check {
  color: green;
}

</style>
