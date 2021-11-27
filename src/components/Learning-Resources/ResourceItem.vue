<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button @click="deleteItem">Delete</base-button>
      </header>
      <p>{{ description }}</p>
      <nav>
        <a :href="link">View Resource</a>
      </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  inject: ["deleteIt"],
  props: ["title", "description", "link", "id"],
  data() {
    return {};
  },

  methods: {
    deleteItem() {
      this.deleteIt(this.id);
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
header h3 {
  text-transform: uppercase;
}
p {
  padding: 1rem 0;
}
</style>
