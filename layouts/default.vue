<template>
  <v-app id="app">
    <NavBar />
    <v-main class="main">
      <nuxt />
      <v-footer
        v-if="$vuetify.breakpoint.mdAndUp"
        class="justify-center pl-0"
        inset
        app
      >
        <span>&copy; 2021</span>
      </v-footer>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'default',
  middleware: 'auth',
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;400;700&display=swap');

.v-application {
  font-family: 'Poppins', sans-serif !important;
}
.v-card__title {
  font-weight: 600;
  color: #686868;
}
.v-card__subtitle {
  color: grey;
}
.v-card__text {
  color: grey;
}
.v-btn {
  font-weight: 500;
}
p {
  color: #686868;
}
h1 {
  color: #686868;
}
h2 {
  color: #686868;
}
h3 {
  color: #686868;
}
h4 {
  color: #686868;
}
h5 {
  color: #686868;
}
.bounce-enter-active {
  transform-origin: top;
  animation: bounce-in 0.8s;
}
.bounce-leave-active {
  transform-origin: top;
  animation: bounce-out 0.5s;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}
@keyframes bounce-out {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(0);
  }
}

</style>
