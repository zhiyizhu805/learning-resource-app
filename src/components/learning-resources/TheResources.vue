<template>
  <base-card>
    <!-- attribut fall through -->
    <!-- dynamically bind mode prop with computed property -->
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resources</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="seletedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      seletedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The Official Guide to Vue.js',
          link: 'https://vuejs.org/v2/guide/',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Google Search Engine',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResourceItem: this.addResourceItem,
      removeResource:this.removeResource
    };
  },
  computed: {
    storedResButtonMode() {
      return this.seletedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.seletedTab === 'add-resource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.seletedTab = tab;
    },
    addResourceItem(title, description, url) {
      const newResourceItem = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        url: url,
      };
      this.storedResources.unshift(newResourceItem);
      this.seletedTab = 'stored-resources';
    },
    removeResource(id){
    //   when you use provide/inject approach, DO NOT create a new array since the new array will not be 're-provide' to other componenent,
    //   so you cannot use filer method.
    //  this.storedResources = this.storedResources.filter(res=>res.id != id)
    
    //splice will work on the orignal array.
    const resIndex = this.storedResources.findIndex(res=>res.id === id)
    this.storedResources.splice(resIndex,1)
  },}
};
</script>
