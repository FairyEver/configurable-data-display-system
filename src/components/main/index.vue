<template>
  <div>
    <div>
      <Header></Header>
    </div>
    <div>
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
export default {
  components: {
    Header: () => import('./_Header.vue')
  }
}
</script>
