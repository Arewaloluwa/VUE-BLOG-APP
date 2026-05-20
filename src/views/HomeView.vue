<script setup>
import { ref, onMounted } from "vue"

const posts = ref([])

const loading = ref(true)

const error = ref(null)

const fetchPosts = async () => {

  try {

    const response = await fetch(
      "https://api.oluwasetemi.dev/posts"
    )

    if (!response.ok) {
      throw new Error(
        "Failed to fetch posts"
      )
    }

    const data = await response.json()

    posts.value = data

  } catch (err) {

    error.value = err.message

  } finally {

    loading.value = false
  }
}

onMounted(() => {
  fetchPosts()
})
</script>

<template>

  <main class="home">

    <section class="hero">

      <h1>
        Finance Insight Blog
      </h1>

      <p>
        Learn investing, budgeting,
        saving and wealth creation.
      </p>

    </section>

    <section class="posts-container">

      <div
        v-if="loading"
        class="status"
      >
        Loading posts...
      </div>

      <div
        v-else-if="error"
        class="status error"
      >
        {{ error }}
      </div>

      <div
        v-else
        class="grid"
      >

        <div
          class="card"
          v-for="post in posts"
          :key="post.id"
        >

          <img
            src="https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3"
            alt="finance"
          />

          <div class="card-content">

            <h2>
              {{ post.title }}
            </h2>

            <p>
              {{ post.body.substring(0, 100) }}...
            </p>

            <RouterLink
              :to="`/post/${post.id}`"
            >

              <button>
                Read Article
              </button>

            </RouterLink>

          </div>

        </div>

      </div>

    </section>

  </main>

</template>

<style scoped>

.home {
  background: #f4f7fb;
  min-height: 100vh;
}

.hero {
  text-align: center;
  padding: 60px 20px;
  background: linear-gradient(
    to right,
    #0f172a,
    #1e293b
  );
  color: white;
}

.hero h1 {
  font-size: 50px;
  margin-bottom: 10px;
}

.hero p {
  font-size: 18px;
}

.posts-container {
  padding: 40px;
}

.grid {
  display: grid;

  grid-template-columns:
    repeat(auto-fit, minmax(300px, 1fr));

  gap: 30px;
}

.card {
  background: white;
  border-radius: 15px;

  overflow: hidden;

  box-shadow:
    0 5px 15px rgba(0,0,0,0.1);

  transition: 0.3s;
}

.card:hover {
  transform: translateY(-8px);
}

.card img {
  width: 100%;
  height: 220px;
  object-fit: cover;
}

.card-content {
  padding: 20px;
}

.card h2 {
  margin-bottom: 10px;
  color: #0f172a;
}

.card p {
  color: #555;
  margin-bottom: 20px;
}

button {
  background: #0f172a;
  color: white;

  border: none;

  padding: 12px 18px;

  border-radius: 8px;

  cursor: pointer;
}

button:hover {
  background: #1e293b;
}

.status {
  text-align: center;
  font-size: 20px;
}

.error {
  color: red;
}

</style>