<template>
  <el-form-item label="资源地址：">
    <el-input v-model="tempValue" type="textarea" :rows="3" placeholder="请输入url地址" />
  </el-form-item>
</template>

<script>
export default {
  name: "attr-qk-musicSrc",
  props: {
    musicSrc: String
  },
  data() {
    return {
      tempValue: ""
    };
  },
  watch: {
    musicSrc(val) {
      this.tempValue = val;
    },
    tempValue() {
      this.$emit("update:musicSrc", this.tempValue);
    }
  },
  mounted() {
    this.tempValue = this.musicSrc;
  }
};
</script>

<style scoped>
</style>
