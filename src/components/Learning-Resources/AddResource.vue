<template>
  <base-error v-if="inputIsInvalid" title="Error" to="body" @close="closeModal">
    <template v-slot:default>
      <p>Atleast one input value is invalid.Please fill out all the inputs</p>
    </template>
    <template v-slot:btns>
      <base-button @click="closeModal" mode="flat">Okay</base-button>
    </template>
  </base-error>
  <base-card>
    <form>
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" name="title" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          name="description"
          id="description"
          cols="30"
          rows="3"
          ref="descriptionInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" id="link" name="link" ref="linkInput" />
      </div>
      <div>
        <base-button type="submit" @click.prevent="submitData"
          >Add Resource</base-button
        >
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ["addRes"],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDes = this.$refs.descriptionInput.value;
      const enteredLink = this.$refs.linkInput.value;

      if (
        enteredTitle.trim() === "" ||
        enteredDes.trim() === "" ||
        enteredLink.trim() === ""
      ) {
        this.inputIsInvalid = true;
        return;
      }
      this.addRes(enteredTitle, enteredDes, enteredLink);
    },
    closeModal() {
      this.inputIsInvalid = false;
    },
  },
};
</script>

<style scoped>
.form-control label {
  display: block;
}
.form-control {
  margin: 1rem 0;
}
input,
textarea {
  display: block;
  width: 100%;
  padding: 0.15rem;
  border: 1px solid #ccc;
}
input:focus,
textarea:focus {
  outline: none;
  border-color: #000;
  background: #f7ebff;
}

base-button {
  margin-top: 1rem;
}
</style>
