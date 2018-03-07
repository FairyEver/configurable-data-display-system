<template>
  <div :style="stageStyle" class="stage">
    viewer
  </div>
</template>

<script>
export default {
  name: 'cdds-maker',
  props: {
    // 单位尺寸
    cell: {
      type: Number,
      required: false,
      default: 1
    },
    // 宽度
    width: {
      type: Number,
      required: false,
      default: 192
    },
    // 高度
    height: {
      type: Number,
      required: false,
      default: 108
    }
  },
  computed: {
    stageStyle () {
      return {
        width: this.cell * this.width + 'px',
        height: this.cell * this.height + 'px'
      }
    }
  }
}
</script>

<style scoped>
.stage {
  background-color: #333;
}
</style>
