<template>
  <div class="maker" :style="style">
    <div class="left">
      <cdds-maker-page-list
        :pages="currentPages"
        :active="pageActive"
        @select="handlePageListSelect"
        @add="handlePageListAdd">
      </cdds-maker-page-list>
    </div>
    <div class="main">main</div>
    <div class="right"></div>
  </div>
</template>

<script>
export default {
  name: 'cdds-maker',
  components: {
    CddsMakerPageList: () => import('./components/pageList')
  },
  props: {
    // 整个编辑器的高度
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
      currentPages: [],
      // 现在激活的页面
      pageActive: null
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
    // 外部参数变化了 更新内部值
    updateCurrent () {
      console.log('updateCurrent')
      this.currentStageCell = this.stageCell
      this.currentStageHeight = this.stageHeight
      this.currentStageWidth = this.stageWidth
      this.currentPages = this.pages
    },
    // 接收页面列表的选中事件
    handlePageListSelect (index) {
      this.pageActive = index
    },
    // 接收页面列表的新建页面事件
    handlePageListAdd ({type, name}) {
      console.log('新建页面', name, type)
      this.currentPages.push({
        title: name,
        type
      })
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
  overflow: auto;
}
.maker .main {
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 200px;
  right: 200px;
  overflow: auto;
}
.maker .right {
  position: absolute;
  top: 0px;
  bottom: 0px;
  right: 0px;
  width: 200px;
  overflow: auto;
}
</style>
