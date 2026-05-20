<template>
  <nav class="navbar">
    <div class="logo">FinanceBlog</div>
    <div class="nav-links">
      <RouterLink to="/">Home</RouterLink>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  background: #020617;
  color: white;
  padding: 20px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 24px;
  font-weight: bold;
}

.nav-links a {
  color: white;
  text-decoration: none;
  font-size: 18px;
  margin-left: 24px;
}

.nav-links a:hover {
  color: #38bdf8;
}
</style>
