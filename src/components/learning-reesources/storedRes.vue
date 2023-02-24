<template>
     <ul>
    <learning-resource
      v-for="res in Res"
      :key="res.id"
      :id="res.id"
      :title="res.title"
      :desc="res.description"
      :link="res.link"
    ></learning-resource>
  </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';

export default {
    inject: ['Res'],

    components: {
        LearningResource
    }
}
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