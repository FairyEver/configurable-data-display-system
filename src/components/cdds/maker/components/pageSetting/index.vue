<template>
  <div style="padding: 0px 10px 10px 10px;">
    <Button type="error" long @click="$emit('delete')">
      <Icon type="trash-a"></Icon>
      删除
    </Button>
  </div>
</template>
