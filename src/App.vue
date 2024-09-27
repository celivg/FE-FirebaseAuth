<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { signOut } from 'firebase/auth'
import { $auth } from '@/firebaseApp'
import { useRouter } from 'vue-router'

const router = useRouter()

async function handleSignOut() {
  signOut($auth).then(() => {
    alert('Cerraste Sesión')
    router.push({ name: 'login' })
  })
}
</script>

<template>
  <div class="container">
    <nav>
      <RouterLink :to="{ name: 'home' }">Home</RouterLink>
      <RouterLink :to="{ name: 'login' }">Login</RouterLink>
      <RouterLink :to="{ name: 'register' }">Sign Up</RouterLink>
      <button class="btn" @click="handleSignOut">Sign Out</button>
    </nav>
  </div>

  <RouterView />
</template>

<style scoped>
.container {
  background-color: #ea5d5d;
  padding: 1rem;
}
nav {
  display: flex;
  justify-content: end;
  align-items: center;
  gap: 1rem;
  margin-right: 5rem;
}

nav a {
  color: #ffffff;
  text-decoration: none;
}

nav a:hover {
  text-decoration: underline;
}

.btn {
  padding: 0.5rem 1rem;
  background-color: #333;
  color: #fff;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
}
</style>
