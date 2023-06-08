<template>
  <h1>To Do List</h1>
</template>

<style scoped>
h1 {
  position: absolute;
  color: white;
  top: 10vh;
  left: 50%;
  transform: translate(-50%, -50%);
  text-transform: uppercase;
  font-weight: 300;
  letter-spacing: 2px;
  padding: 5px;
  animation: slide-down 300ms ease-out forwards;
  animation-delay: 300ms;
  opacity: 0;
}

@keyframes slide-down {
  from {
    opacity: 0;
    transform: translate(-50%, -60%);
  }
  to {
    opacity: 75%;
    transform: translate(-50%, -50%);
  }
}

@media (max-width: 768px) {
  h1 {
    font-size: 1.5rem;
  }
}
</style>
