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
      @click="handleAdd">
      新建页面
    </Button>
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
  methods: {
    // 接收点击页面的事件
    handlePageClick (index) {
      // 将事件传递出去
      this.$emit('select', index)
    },
    // 接收新建页面的事件
    handleAdd () {
      // 将事件传递出去
      this.$emit('add')
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
