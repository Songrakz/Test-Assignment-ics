<template>
  <v-app>
    <v-main class="bg">
      <Navbar />
      <Sidebar />
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Sidebar from './components/Sidebar.vue';
export default {
  components: {
    Navbar,
    Sidebar,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Kanit:wght@400;500&display=swap');
* {
  font-family: 'Kanit', sans-serif;
}
.bg {
  background-color: #f5f6f8;
}

</style>