<template>
  <div class="header">
    <router-link :to="{name: 'dashboard'}">dashboard</router-link>
  </div>
</template>

<style scoped>
.header {
  background-color: #000;
  height: 30px;
  line-height: 30px;
  padding: 0px 10px;
}
.header a {
  color: #FFF;
}
</style>
