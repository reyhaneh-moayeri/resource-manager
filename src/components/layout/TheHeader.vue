<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ["title"],
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: center;
  background: darkblue;
  color: #fff;
  padding: 3rem 0;
}
</style>
