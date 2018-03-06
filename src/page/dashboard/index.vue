<template>
  <div>
    <!-- 编辑器 -->
    <cdds-maker
      height="calc(100vh - 30px)">
    </cdds-maker>
  </div>
</template>

<script>
export default {
  components: {
    CddsMaker: () => import('@/components/cdds/maker/index.vue')
  }
}
</script>
