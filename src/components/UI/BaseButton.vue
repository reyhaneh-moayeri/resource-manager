<template>
  <button :type="type" :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ["type", "mode"],
};
</script>

<style scoped>
button {
  border: none;
  background: #ccc;
  padding: 1rem;
  margin-right: 0.5rem;
  cursor: pointer;
  transition: all 0.5s ease-in-out;
  margin-top: 1rem;
}
.flat {
  background: darkblue;
  color: #fff;
}
</style>
