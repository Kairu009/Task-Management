<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <header>
    <div class="logo-wrapper">
      <img
        alt="Vue logo"
        class="logo"
        src="@/assets/logo.svg"
        width="125"
        height="125"
      />
      <HelloWorld msg="Task Manager" />
    </div>

    <div class="nav-wrapper">
      <nav>
        <RouterLink to="/">Tasks</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.6;
  max-height: 100vh;
}

.logo-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.logo {
  margin-right: 1rem;
}

.nav-wrapper {
  width: 100%;
  display: flex;
  justify-content: center;
}

nav {
  margin-bottom: 2rem;
  font-size: 12px;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (max-width: 768px) {
  .logo-wrapper {
    flex-direction: column; /* Change direction to column for smaller screens */
    align-items: center;
  }

  .logo {
    margin-right: 0; /* Remove margin on smaller screens */
    margin-bottom: 1rem; /* Add margin bottom for spacing */
  }
}
</style>
