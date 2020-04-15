<template>
  <el-form-item label="文本内容：">
    <el-input
      v-model="tempText"
      type="textarea"
      :rows="2"
      placeholder="请输入文本内容"
    />
  </el-form-item>
</template>

<script>
	export default {
		name: "attr-qk-text",
		props: {
			text: String
		},
		data() {
			return {
				tempText: ''
			}
		},
		watch: {
			text() {
				this.tempText = this.text;
			},
			tempText() {
				this.$emit('update:text', this.tempText)
			}
		},
		mounted() {
			this.tempText = this.text;
		}
	}
</script>

<style scoped>

</style>
