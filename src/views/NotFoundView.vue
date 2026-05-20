<template>

  <div class="not-found">

    <h1>404</h1>

    <p>
      The page you are looking for does not exist.
    </p>

    <RouterLink to="/">
      <button>
        Return Home
      </button>
    </RouterLink>

  </div>

</template>

<style scoped>

.not-found {
  height: 100vh;

  display: flex;
  flex-direction: column;

  justify-content: center;
  align-items: center;

  background: #f8fafc;
}

h1 {
  font-size: 100px;
  color: #0f172a;
}

p {
  margin: 20px 0;
  color: #475569;
}

button {
  background: #0f172a;
  color: white;

  border: none;
  padding: 14px 20px;

  border-radius: 8px;
  cursor: pointer;
}

</style>