<template>
  <base-card>
    <base-button
      @click="setSelectedTab('learning-resources')"
      :mode="resourcesButtonMode"
      >Learning Resources
    </base-button>
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResourceButtonMode"
      >Add Resource
    </base-button>
  </base-card>
  <keep-alive>
    <component
      :is="selectedTab"
      @delete-resource="deleteResource"
      @add-resource="addResource"
    ></component>
  </keep-alive>
</template>

<script>
import AddResource from "./AddResource.vue";
import LearningResources from "./LearningResources.vue";

let id = 0; // Used for resource ID

export default {
  components: {
    LearningResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: "learning-resources",
      storedResources: [
        {
          id: ++id,
          title: "Official Guide",
          description: "The official Vue.js documentation.",
          link: "https://vuejs.org",
        },
        {
          id: ++id,
          title: "Google",
          description: "Learn how to google.",
          link: "https://google.com",
        },
      ],
    };
  },
  provide() {
    return {
      storedResources: this.storedResources,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(resource) {
      this.storedResources.unshift(resource);
      this.selectedTab = "learning-resources";
    },
    deleteResource(id) {
      const index = this.storedResources.findIndex(
        (resource) => resource.id === id
      );
      if (index > -1) {
        this.storedResources.splice(index, 1);
      }
    },
  },
  computed: {
    resourcesButtonMode() {
      return this.selectedTab === "learning-resources" ? "" : "flat";
    },
    addResourceButtonMode() {
      return this.selectedTab === "add-resource" ? "" : "flat";
    },
  },
};
</script>
