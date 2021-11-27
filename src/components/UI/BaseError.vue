<template>
  <div class="overlay" @click="$emit('close')">
    <dialog open>
      <header>
        <slot name="header">
          <h2>{{ title }}</h2>
        </slot>
      </header>
      <section>
        <slot></slot>
      </section>
      <div>
        <slot name="btns"></slot>
      </div>
    </dialog>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      required: false,
      type: String,
    },
  },
};
</script>

<style scoped>
.overlay {
  width: 100%;
  height: 100%;
  position: fixed;
  background-color: rgba(0, 0, 0, 0.5);
  top: 0;
  left: 0;
}
dialog {
  border: none;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 3rem;
  border-radius: 1rem;
}

header {
  margin-bottom: 1rem;
}
</style>
