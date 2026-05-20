<script setup>
import Navbar from "./components/Navbar.vue"
</script>

<template>

  <Navbar />

  <Suspense>

    <template #default>
      <RouterView />
    </template>

    <template #fallback>

      <div class="loading">
        Loading content...
      </div>

    </template>

  </Suspense>

</template>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
}

.loading {
  padding: 50px;
  text-align: center;
  font-size: 20px;
}

</style>