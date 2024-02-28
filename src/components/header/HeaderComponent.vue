<script setup>
import { useRoute, useRouter } from "vue-router";

const route = useRoute()
const router = useRouter()

const isLoggedIn = false; 
const isLoginPage = router.currentRoute.value.name === 'login'; 

const toggleAuth = () => {
  if (isLoggedIn) {
    logout();
  } else {
    goToLogin();
  }
}


const goToLogin = () => {
  router.push('/login');
}

const logout = () => {
  router.push({ name: 'home' })
}

// const goToHome = () => {
//   router.push('/');
// }
</script>
  
<template>
    <header>
      <img src="../../assets/images/icons/logoHeader.png" alt="">
      
      <div class="buttons">

    

        <v-btn class="button1" color="orange-darken-1" @click="toggleAuth">
        {{ isLoggedIn ? 'Cerrar Sesión' : 'Iniciar Sesión' }}
      </v-btn>
        <v-btn class="button1" color="orange-darken-1" v-if="isLoggedIn && !isLoginPage" @click="logout">Home</v-btn>
        <v-btn class="button2" color="orange-darken-1">registrarse</v-btn>

      </div>
    </header> 
</template> 

<style lang="scss" scoped>
 header {
   background-color:#80CBC4;
   width: 100%;
   height: 150px;
   display: flex;
   justify-content: space-between;
  }

  .buttons {
    margin-top: 80px;
    margin-right: 50px;
  }

  .button1 {
    margin-right: 25px;
  }

</style>