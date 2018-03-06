<template>
  <div class="maker" :style="style">
    <div class="left">
      <cdds-maker-page-list
        :pages="pages"
        @select="handlePageListSelect"
        @add="handlePageListAdd">
      </cdds-maker-page-list>
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
    },
    // 舞台设置
    stageCell: {
      type: Number,
      required: false,
      default: 0
    },
    stageHeight: {
      type: Number,
      required: false,
      default: 0
    },
    stageWidth: {
      type: Number,
      required: false,
      default: 0
    },
    // 页面设置
    pages: {
      type: Array,
      required: false,
      default: () => []
    }
  },
  data () {
    return {
      // 私有舞台设置
      currentStageCell: 0,
      currentStageHeight: 0,
      currentStageWidth: 0,
      // 私有页面设置
      currentPages: {}
    }
  },
  computed: {
    // 容器的样式
    style () {
      return {
        height: this.height
      }
    }
  },
  methods: {
    // 接收页面列表的选中事件
    handlePageListSelect (index) {
      console.log(index)
    },
    // 接收页面列表的新建页面事件
    handlePageListAdd () {
      console.log('新建页面')
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
