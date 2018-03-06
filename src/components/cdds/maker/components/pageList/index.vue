<template>
  <div class="page-list">
    <ul>
      <li
        v-for="(item, index) in pages"
        :key="index"
        @click="handlePageClick(index)">
        {{item.title}}
      </li>
    </ul>
    <Button
      size="large"
      long
      @click="addTypeModal = true">
      新建页面
    </Button>
    <Modal
      width="300"
      title="新建类型"
      v-model="addTypeModal">
      <Button
        @click="handleSelectAddPageType('grid')">
        网格布局
      </Button>
      <Button
        @click="handleSelectAddPageType('free')">
        自由布局
      </Button>
      <div slot="footer">
        <Button type="text" long @click="addTypeModal = false">取消</Button>
      </div>
    </Modal>
  </div>
</template>

<script>
export default {
  name: 'cdds-maker-page-list',
  props: {
    pages: {
      type: Array,
      required: false,
      default: () => []
    }
  },
  data () {
    return {
      // 新建类型模态框
      addTypeModal: false
    }
  },
  methods: {
    // 接收点击页面的事件
    handlePageClick (index) {
      // 将事件传递出去
      this.$emit('select', index)
    },
    // 接收选择新建页面类型按钮的事件
    handleSelectAddPageType (type) {
      // 关闭模态框
      this.addTypeModal = false
      // 将事件传递出去
      this.$emit('add', type)
    }
  }
}
</script>

<style scoped>
.page-list {
  padding: 10px;
}
.page-list ul{
  list-style: none;
  margin: 0px;
  padding: 0px;
}
.page-list ul li {
  display: block;
  height: 100px;
  line-height: 100px;
  text-align: center;
  border-radius: 4px;
  border: 1px solid #CCC;
  cursor: pointer;
  user-select: none;
  margin-bottom: 10px;
}
.page-list ul li:hover {
  background-color: #F7F7F7;
  border: 1px solid #666;
}
</style>
