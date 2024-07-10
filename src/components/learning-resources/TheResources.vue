<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resource')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resources</base-button
    >
  </base-card>
  <keep-alive><component :is="selectedTab"></component></keep-alive>
</template>

<script>
import StoredResource from './StoredResource.vue';
import AddResource from './AddResource.vue';
export default {
  components: { StoredResource, AddResource },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'the offcial Vue.js documentation.',
          link: 'https://vuejs.org',
        },

        {
          id: 'google',
          title: 'Google',
          description: 'Search anything on google.',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.removeResource,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resource' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResources.push(newResource);
      this.selectedTab = 'stored-resource';
    },

    removeResource(resId) {
      const resIndex = this.storedResources.findIndex(
        (res) => res.id === resId
      );

      this.storedResources.splice(resIndex, 1);
    },
  },
};
</script>
