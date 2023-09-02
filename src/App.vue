<template>
  <div id="app">
    <div class="logo">
      <img class="logo" src="../src/assets/logo.png" alt="">
    </div>
    <MainComponent />
  </div>
</template>

<script>

import MainComponent from '@/components/MainComponent.vue'
export default {
  name: 'App',
  components: {
    MainComponent
  }
}
</script>

<style lang="scss">
.logo {
  text-align: center;
}
</style>
