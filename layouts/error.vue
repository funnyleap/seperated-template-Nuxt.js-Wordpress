<template>
  <div class="error-container">
    <h2 class="error-code align-center">{{ error.statusCode }}</h2>
    <p class="error-text align-center">{{ error.message }}</p>
  </div>
</template>
<script>
export default {
  name: 'NuxtError',
  props: ['error'],
  layout: 'page',
  created () {
    this.$store.commit('UPDATE_ERROR_MESSAGE', { code: this.error.statusCode, message: this.error.message })
  },
  beforeDestroy () {
    this.$store.commit('UPDATE_ERROR_MESSAGE', { code: null, message: '' })
  }
}
</script>
<style lang="scss" scoped>
.error-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-top: 200px;

  .error-code {
    font-size: 30px;
  }
}
</style>
