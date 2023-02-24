<template>
<the-header title="Programming Resources"></the-header>
<the-res></the-res>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheRes from './components/learning-reesources/TheRes.vue';
export default {
  components: {
    TheHeader,
    TheRes
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