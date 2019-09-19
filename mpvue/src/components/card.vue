<template>
  <div>
    <p class="card">
      {{text}}
    </p>
  </div>
</template>

<script>
export default {
  props: ['text']
}
</script>

<style lang="less" scoped>
.card {
  text-align: center;
  padding: 10px;
}
</style>
