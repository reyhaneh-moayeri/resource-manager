<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storeResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource";
export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: "stored-resources",
      storedResources: [
        {
          id: "0",
          title: "official-guid",
          description: "The official Vue js documentation",
          link: "https://vuejs.org",
        },
        {
          id: "1",
          title: "Google",
          description:
            "You have to know how to find your problems answer in google",
          link: "https://google.com",
        },
      ],
    };
  },
  computed: {
    storeResButtonMode() {
      return this.selectedTab === "stored-resources" ? "flat" : null;
    },
    addResButtonMode() {
      return this.selectedTab === "add-resource" ? "flat" : null;
    },
  },
  provide() {
    return {
      res: this.storedResources,
      addRes: this.addResource,
      deleteIt: this.deleteData,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, des, link) {
      const newResourceObj = {
        id: new Date().getMilliseconds().toString,
        title: title,
        description: des,
        link: link,
      };

      this.storedResources.unshift(newResourceObj);
      this.selectedTab = "stored-resources";
    },
    deleteData(Id) {
      const resIndex = this.storedResources.findIndex((res) => res.id === Id);
      this.storedResources.splice(resIndex, 1);
    },
  },
};
</script>
