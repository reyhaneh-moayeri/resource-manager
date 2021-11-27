<template>
  <ul>
    <resource-item
      v-for="resource in res"
      :id="resource.id"
      :key="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
    ></resource-item>
  </ul>
</template>

<script>
import ResourceItem from "./ResourceItem.vue";
export default {
  inject: ["res"],
  components: { ResourceItem },
};
</script>

<style scoped>
ul {
  max-width: 40rem;
  list-style: none;
  margin: 2rem auto;
}
</style>
