<!--test.vue-->
<template>
  <div class="qk-input">
    <input v-model="value" class="qk-input-item" :placeholder="placeholder" type="text">
  </div>
</template>

<script>
export default {
  name: 'QkInput',
  props: {
    placeholder: {
      type: String,
      default: '请输入'
    },
    value: {
      require: false
    }
  },
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
.qk-input-item {
  display: block;
  width: 100%;
  height: 100%;
  outline: none;
  border: none;
}
</style>
