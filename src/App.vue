<template>
  <the-header title="Resource Manager"></the-header>
  <the-resources></the-resources>
</template>

<script>
import TheHeader from "./components/layout/TheHeader.vue";
import TheResources from "./components/Learning-Resources/TheResources.vue";
export default {
  components: {
    TheResources,
    TheHeader,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  font-family: "Roboto", sans-serif;
}
</style>
