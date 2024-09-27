<script setup>
import { GoogleAuthProvider, signInWithPopup } from 'firebase/auth'
import { $auth } from '@/firebaseApp'

async function handleGoogleRegister() {
  try {
    const provider = new GoogleAuthProvider()
    await signInWithPopup($auth, provider)
  } catch (error) {
    console.error(error)
  }
}
</script>

<template>
  <button class="btn-google" @click="handleGoogleRegister">
    <img
      src="https://cdn-icons-png.flaticon.com/512/300/300221.png"
      alt=""
      width="20"
      :style="{ marginRight: '1rem' }"
    />Registrarme con Google
  </button>
</template>

<style scoped>
.btn-google {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #ffffff;
  color: #ea5d5d;
  border: 2px solid #ea5d5d;
  border-radius: 0.5rem;
  padding: 1rem 3rem;
}
</style>
