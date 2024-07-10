<template>
  <the-header title="OlaRemMe"></the-header>
  <the-resources></the-resources>
  <!-- <ul>
    <learning-resource
      v-for="res in storedResources"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    ></learning-resource>
  </ul> -->
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';
// import LearningResource from './components/learning-resources/LearningResource.vue';
// components: { TheHeader },
export default {
  components: { TheHeader, TheResources },
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
