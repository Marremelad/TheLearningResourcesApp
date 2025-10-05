<template>
  <base-card>
    <form @submit.prevent>
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" name="title" ref="title" />
      </div>
      <div class="form-control">
        <label for="description">Title</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="description"
        />
      </div>
      <div class="form-control">
        <label for="link">Title</label>
        <input type="url" id="link" name="link" ref="link" />
      </div>
      <div>
        <base-button type="submit" @click="addResource"
          >Add Resource</base-button
        >
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  emits: ["add-resource"],
  methods: {
    addResource() {
      this.$emit("add-resource", {
        title: this.$refs.title.value,
        description: this.$refs.description.value,
        link: this.$refs.link.value,
      });
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

textarea {
  resize: none;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
