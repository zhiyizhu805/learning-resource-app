<template>
  <stored-resources :resources = "storedResources" ></stored-resources>
</template>

<script>
import StoredResources from './components/learning-resources/StoredResources.vue';

export default {
  components: {
    StoredResources,
  },
  data() {
    return {
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
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}

</style>