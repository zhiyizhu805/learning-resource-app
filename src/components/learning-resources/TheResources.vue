<template>
  <base-card>
    <!-- attribut fall through -->
    <!-- dynamically bind mode prop with computed property -->
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode" 
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode"
      >Add Resources</base-button
    >
  </base-card>
  <component :is="seletedTab" @add-resource-item = "addResourceItem"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue'
export default {
  components: {
    StoredResources,
    AddResource
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
    };
  },
  computed:{
    storedResButtonMode(){
        return this.seletedTab === 'stored-resources' ? null : 'flat'
    },
    addResButtonMode(){
        return this.seletedTab === 'add-resource' ? null : 'flat'

    }
  },
  methods: {
    setSelectedTab(tab) {
      this.seletedTab = tab;
    },
    addResourceItem(title,description,link){
        const newResourceItem = {
            id : title,
            title : title,
            description: description,
            link : link 
        }
        this.storedResources.unshift(newResourceItem)

    }
  },
};
</script>
