<template>
  <the-header title="RememberMe"></the-header>
  <the-resources></the-resources>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';

export default {
  components: {
    TheHeader,
    TheResources
  },
  data() {
    return {
      // storedResources: [
      //   {
      //     id: 'official-guide',
      //     title: 'Official Guide',
      //     description: 'The Official Guide to Vue.js',
      //     link: 'https://vuejs.org/v2/guide/',
      //   },
      //   {
      //     id: 'google',
      //     title: 'Google',
      //     description: 'Google Search Engine',
      //     link: 'https://google.com',
      //   },
      // ],
    };
  },
  // provide() {
  //   return {
  //     resource: this.storedResources,
  //   };
  // },
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
