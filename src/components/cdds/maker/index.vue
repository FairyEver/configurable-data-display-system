<template>
  <div class="maker" :style="style">
    <div class="left">
      <cdds-maker-page-list></cdds-maker-page-list>
    </div>
    <div class="main">main</div>
    <div class="right">right</div>
  </div>
</template>

<script>
export default {
  name: 'cdds-maker',
  components: {
    CddsMakerPageList: () => import('./components/pageList')
  },
  props: {
    height: {
      type: String,
      required: false,
      default: '500px'
    }
  },
  computed: {
    // 容器的样式
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
  position: relative;
}
.maker .left {
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 0px;
  width: 200px;
}
.maker .main {
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 200px;
  right: 200px;
}
.maker .right {
  position: absolute;
  top: 0px;
  bottom: 0px;
  right: 0px;
  width: 200px;
}
</style>
