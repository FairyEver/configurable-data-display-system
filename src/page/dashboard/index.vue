<template>
  <div>
    <!-- 编辑器 -->
    <cdds-maker></cdds-maker>
  </div>
</template>

<script>
export default {
  components: {
    CddsMaker: () => import('@/components/cdds/maker/index.vue')
  }
}
</script>
