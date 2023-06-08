<template>
  <h1>Lista Zadań</h1>
</template>

<style scoped>
h1 {
  padding: 2rem 0;
  color: white;
  text-align: center;
  text-transform: uppercase;
  font-weight: 300;
  letter-spacing: 2px;
  animation: slide-down 300ms ease-out forwards;
  opacity: 0;
}

@keyframes slide-down {
  from {
    opacity: 0;
  }
  to {
    opacity: 75%;
  }
}

@media (max-width: 768px) {
  h1 {
    font-size: 1.5rem;
  }
}
</style>
