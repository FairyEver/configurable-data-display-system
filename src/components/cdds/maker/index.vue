<template>
  <div class="maker" :style="style">
    <!-- 页面列表 -->
    <div class="left">
      <cdds-maker-page-list
        :pages="currentPages"
        :active="pageActive"
        @select="handlePageListSelect"
        @add="handlePageListAdd">
      </cdds-maker-page-list>
    </div>
    <!-- 工具栏 -->
    <div class="main-header">main-header</div>
    <!-- 预览窗口 主要 -->
    <div class="main">
      <div v-if="pageActive === null" class="info-choose-page">请先选择一个页面</div>
    </div>
    <!-- 右侧菜单 -->
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
/* 主要的左中右布局 */
.maker .left {
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 0px;
  width: 200px;
  overflow: auto;
}
.maker .main-header {
  position: absolute;
  top: 0px;
  left: 200px;
  right: 300px;
  height: 30px;
  border-left: 1px solid #dddee1;
  border-right: 1px solid #dddee1;
  border-bottom: 1px solid #dddee1;
}
.maker .main {
  position: absolute;
  top: 30px;
  bottom: 0px;
  left: 200px;
  right: 300px;
  overflow: auto;
  border-left: 1px solid #dddee1;
  border-right: 1px solid #dddee1;
}
.maker .right {
  position: absolute;
  top: 0px;
  bottom: 0px;
  right: 0px;
  width: 300px;
  overflow: auto;
}
/* 请选择一个页面的提示 */
.info-choose-page {
  height: 30px;
  line-height: 30px;
  width: 200px;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  margin-left: -100px;
  margin-top: -15px;
}
</style>
