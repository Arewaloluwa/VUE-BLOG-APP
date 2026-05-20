<script setup>
defineProps({
  post: Object
})
</script>

<template>
  <div class="card">
    <img
      :src="post.image"
      :alt="post.title"
    />

    <div class="card-content">
      <h2>{{ post.title }}</h2>

      <p>
        {{ post.excerpt }}
      </p>

      <RouterLink :to="`/post/${post.id}`">
        <button>Read More</button>
      </RouterLink>
    </div>
  </div>
</template>

<style scoped>
.card {
  border: 1px solid #ddd;
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 10px;
}

a {
  color: blue;
}
</style>