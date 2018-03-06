<template>
  <div class="maker" :style="style">
    maker
  </div>
</template>

<script>
export default {
  props: {
    height: {
      type: String,
      required: false,
      default: '720px'
    }
  },
  computed: {
    style () {
      return {
        height: this.height
      }
    }
  }
}
</script>

<style scoped>
.maker {
  background-color: #CCC;
}
</style>
