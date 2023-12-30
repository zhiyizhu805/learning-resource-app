<template>
  <ul>
    <!--1) use kebab case when use opening and closing tag -->
    <learning-resource
      v-for="resource in resources"
      :key="resource.id"
      :resource="resource"
    ></learning-resource>
  </ul>
</template>

<script>
//3) note the path
import LearningResource from './LearningResource.vue';

export default {
  props: ['resources'],
  components: {
    LearningResource,
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
</style>
