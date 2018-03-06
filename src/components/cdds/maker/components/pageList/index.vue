<template>
  <div>
    list
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
  }
}
</script>
