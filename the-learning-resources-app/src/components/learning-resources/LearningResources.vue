<template>
  <ul>
    <li v-for="resource in storedResources" :key="resource.id">
      <base-card>
        <header>
          <h3>{{ resource.title }}</h3>
          <base-button mode="flat" @click="deleteResource(resource.id)"
            >Delete</base-button
          >
        </header>
        <p>{{ resource.description }}</p>
        <nav>
          <a :href="resource.link">View Resource</a>
        </nav>
      </base-card>
    </li>
  </ul>
</template>

<script>
export default {
  emits: ["delete-resource"],
  inject: ["storedResources"],
  methods: {
    deleteResource(id) {
      this.$emit("delete-resource", id);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}

li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #de4e4e;
}

a:hover,
a:active {
  color: #bd3e3e;
}
</style>
