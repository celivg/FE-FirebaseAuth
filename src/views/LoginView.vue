<script setup>
import { ref } from 'vue'
import { $auth } from '@/firebaseApp'
import { signInWithEmailAndPassword } from 'firebase/auth'
import GoogleButton from '@/components/GoogleButton.vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const email = ref('')
const password = ref('')

async function handleLogin() {
  try {
    await signInWithEmailAndPassword($auth, email.value, password.value)

    email.value = ''
    password.value = ''

    router.push({ name: 'home' })
  } catch (error) {
    console.error(error)
  }
}

async function irARegistrarse() {
  router.push({ name: 'register' })
}
</script>

<template>
  <div class="login">
    <div class="start">
      <h2>Iniciar Sesión</h2>
      <div class="container">
        <div class="box">
          <form @submit.prevent="handleLogin">
            <label for="email">Ingresa tu correo</label>
            <input type="email" id="email" v-model="email" />
            <label for="password">Ingresa tu contraseña</label>
            <input type="password" id="password" v-model="password" />

            <button class="btn" type="submit">Iniciar Sesión</button>
          </form>
          <div class="register">
            <h3>¿No tienes cuenta? ¡Registrate hoy!</h3>
            <button @click="irARegistrarse" class="btn2">Registrarse</button>
            <GoogleButton />
          </div>
        </div>
        <img
          src="https://img.freepik.com/vector-gratis/ilustracion-concepto-colaboracion_114360-3995.jpg?t=st=1727451905~exp=1727455505~hmac=81872db24ee58669dc3bae3010999a29ead47497c6b371b3f8c13c4211ba8a8a&w=996"
          alt=""
          width="600"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
.login {
  margin-top: 5rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.start {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.container {
  display: flex;
  align-items: center;
  gap: 5rem;
}

.box {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 1rem;
  border: 1px solid #333;
  border-radius: 0.5rem;
  width: 40%;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

label {
  font-size: 1.2rem;
}

input {
  padding: 0.5rem;
  font-size: 1rem;
}

.btn {
  padding: 1rem 3rem;
  background-color: #ea5d5d;
  color: #ffffff;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
}

.register {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.btn2 {
  padding: 1rem 3rem;
  background-color: #333;
  color: #fff;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
}

a {
  text-decoration: none;
  color: #fff;
}
</style>
