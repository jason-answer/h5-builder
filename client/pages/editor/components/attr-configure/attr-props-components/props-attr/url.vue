<template>
  <el-form-item label="url地址：">
    <el-input v-model="tempValue" type="textarea" :rows="3" placeholder="请输入url地址" />
  </el-form-item>
</template>

<script>
export default {
  name: 'attr-qk-url',
  props: {
    url: String
  },
  data() {
    return {
      tempValue: ''
    };
  },
  watch: {
    url(val) {
      this.tempValue = val;
    },
    tempValue() {
      this.$emit('update:url', this.tempValue);
    }
  },
  mounted() {
    this.tempValue = this.url;
  }
};
</script>

<style scoped>
</style>
