<template>
  <the-header title="Formularz strony internetowej"></the-header>
  <the-form></the-form>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import TheForm from './components/TheForm.vue';

export default {
  components: {
    TheForm,
    TheHeader
  }  
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: roboto, sans-serif;
}

body {
  margin: 0;
  background-color: #fff;
}
</style>