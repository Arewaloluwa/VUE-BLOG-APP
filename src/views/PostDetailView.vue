<script setup>

import {
  ref,
  onMounted
} from "vue"

import {
  useRoute,
  useRouter
} from "vue-router"

const route = useRoute()

const router = useRouter()

const post = ref(null)

const loading = ref(true)

const error = ref(null)

const fetchPost = async () => {

  try {

    const response = await fetch(
      `https://api.oluwasetemi.dev/posts/${route.params.id}`
    )

    if (!response.ok) {

      throw new Error(
        "Post not found"
      )
    }

    const data = await response.json()

    post.value = data

  } catch (err) {

    error.value = err.message

  } finally {

    loading.value = false
  }
}

onMounted(() => {
  fetchPost()
})

</script>

<template>

  <main class="details">

    <div
      v-if="loading"
      class="status"
    >
      Loading article...
    </div>

    <div
      v-else-if="error"
      class="status error"
    >
      {{ error }}
    </div>

    <div
      v-else
    >

      <img
        src="https://images.unsplash.com/photo-1554224155-6726b3ff858f"
        class="hero-image"
      />

      <div class="content">

        <div class="buttons">

          <button
            @click="router.back()"
          >
            ← Previous Page
          </button>

          <RouterLink to="/">

            <button>
              Home Page
            </button>

          </RouterLink>

        </div>

        <h1>
          {{ post.title }}
        </h1>

        <p>
          {{ post.body }}
        </p>

      </div>

    </div>

  </main>

</template>

<style scoped>

.details {
  min-height: 100vh;
  background: #f8fafc;
}

.hero-image {
  width: 100%;
  height: 400px;
  object-fit: cover;
}

.content {
  max-width: 900px;
  margin: auto;
  padding: 40px 20px;
}

.buttons {
  display: flex;
  gap: 15px;
  margin-bottom: 30px;
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

h1 {
  margin-bottom: 20px;
  font-size: 40px;
  color: #0f172a;
}

p {
  line-height: 1.8;
  font-size: 18px;
  color: #334155;
}

.status {
  text-align: center;
  padding-top: 100px;
  font-size: 24px;
}

.error {
  color: red;
}

</style>