<template>
  <header class="header1">
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ['title'],
};
</script>

<style scoped>
.header1 {
  width: 100%;
  height: 4rem;
  background-color: #161b22;
  display: flex;
  justify-content: center;
  align-items: center;
}

header h1 {
  font-size: 1.3em;
  color: #F0F6fC;
  margin: 0;
  text-shadow: 0px 1px 3px rgb(106, 180, 224);
  cursor: pointer;
}
</style>
