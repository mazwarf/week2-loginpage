<script setup lang="ts">
import { useAuthStore } from '@/stores/auth'
import { useRouter } from 'vue-router';

const auth = useAuthStore()
const router = useRouter()



const onLogout = () => {
  auth.logout()
  router.push('/login')
}

</script>


<template>
  <div class="container">
    <!-- Header -->
    <div class="header">
      <!-- Menu -->
      <div class="menu">
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
        <router-link to="/restricted">|RestrictedPage|</router-link>
      </div>
      <!-- Authenticated User -->
      <div class="AuthenticatedUser">
        <p v-if="auth.username">{{ auth.username }}</p>
        <div v-if="auth.username">
          <button class="logout-btn" @click="onLogout">Logout</button>
        </div>
        <div v-else>
          <router-link class="login-btn" to="/login">Login</router-link>
        </div>
      </div>
    </div>
    <!-- Body -->
    <RouterView></RouterView>
  </div>

</template>
//flex flex-col container mx-auto p-4 gap-10
flex gap-4
flex justify-between
flex gap-2 item-center

<style scoped>


.container {
  display: flex;
  padding: 4px;
  gap: 10px;
  color: pink;
  flex-direction: column;
  font-family: 'Franklin Gothic Medium', sans-serif;
  margin-top: 10px;
  margin-left: 5px;
  margin-right: 5px;
  ;
}

.header {
  display: flex;
  justify-content: space-between;
}
.menu {
  display: flex;
  gap: 5px;
  margin-top: auto;
  color: white;
}

.AuthenticatedUser {
  display: flex;
  gap: 10px;
  
}


.login-btn {
  padding: 5px 15px;
  background-color:  #FF69B4;
  color: black;
  border: none;
  border-radius: 1px;
  cursor: pointer;
  font-size: 15px;
}

.logout-btn {
  padding: 5px 15px;
  background-color:  #FF69B4;
  color: black;
  border: none;
  border-radius: 1px;
  cursor: pointer;
  font-size: 13px;
}


</style>
