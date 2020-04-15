<template>
  <el-form-item label="占位提示文字：">
    <div>
      <el-input v-model="tempText" type="textarea" :rows="2" placeholder="请输入占位提示文字" />
    </div>
  </el-form-item>
</template>

<script>
export default {
  name: "attr-qk-placeholder",
  props: {
    placeholder: String
  },
  data() {
    return {
      tempText: ""
    };
  },
  watch: {
    placeholder(val) {
      this.tempText = val;
    },
    tempText() {
      this.$emit("update:placeholder", this.tempText);
    }
  },
  mounted() {
    this.tempText = this.placeholder;
  }
};
</script>

<style scoped>
</style>
