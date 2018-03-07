<template>
  <div class="maker" :style="style">
    <!-- 页面列表 -->
    <div class="left">
      <cdds-maker-page-list
        :pages="currentPages"
        :active="validPageActive"
        @select="handlePageListSelect"
        @add="handlePageListAdd">
      </cdds-maker-page-list>
    </div>
    <!-- 预览窗口 主要 -->
    <div class="main">
      <div v-if="validPageActive === null" class="info-choose-page">请先选择一个页面</div>
      <cdds-viewer v-if="validPageActive !== null"></cdds-viewer>
    </div>
    <!-- 右侧菜单 -->
    <div class="right">
      <Tabs v-if="validPageActive !== null">
        <TabPane label="页面设置">
          <cdds-page-setting
            :pages="currentPages"
            :active="validPageActive"
            @rename="handlePageRename"
            @delete="handlePageDelete">
          </cdds-page-setting>
        </TabPane>
        <TabPane label="参数设置">标签二的内容</TabPane>
      </Tabs>
    </div>
  </div>
</template>

<script>
export default {
  name: 'cdds-maker',
  components: {
    CddsMakerPageList: () => import('./components/pageList'),
    CddsViewer: () => import('../viewer'),
    CddsPageSetting: () => import('./components/pageSetting')
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
    },
    // 有效的“现在激活的页面” 实际用的都是这个
    validPageActive () {
      if (this.pageActive === null || this.currentPages.length === 0) {
        return null
      } else {
        return this.pageActive < this.currentPages.length ? this.pageActive : this.currentPages.length - 1
      }
    }
  },
  methods: {
    // 外部参数变化了 更新内部值
    updateCurrent () {
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
      this.currentPages.push({
        title: name,
        type
      })
    },
    // 接收更改页面标题的事件
    handlePageRename (newName) {
      this.currentPages[this.validPageActive].title = newName
    },
    // 接收删除页面的事件
    handlePageDelete () {
      this.currentPages.splice(this.validPageActive, 1)
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
/* .maker .main-header {
  position: absolute;
  top: 0px;
  left: 200px;
  right: 300px;
  height: 30px;
  padding-top: 3px;
  padding-left: 3px;
  border-left: 1px solid #dddee1;
  border-right: 1px solid #dddee1;
  border-bottom: 1px solid #dddee1;
} */
.maker .main {
  position: absolute;
  top: 0px;
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
