<template>
  <el-form-item label="图片：">
    <imageSelect :url.sync="tempValue" />
  </el-form-item>
</template>

<script>
import imageSelect from '@client/components/image-select';
export default {
  name: 'attr-qk-imageSrc',
  components: {
    imageSelect
  },
  props: {
    imageSrc: String
  },
  data() {
    return {
      tempValue: ''
    };
  },
  watch: {
    imageSrc(val) {
      this.tempValue = val;
    },
    tempValue() {
      this.$emit('update:imageSrc', this.tempValue);
    }
  },
  mounted() {
    this.tempValue = this.imageSrc;
  }
};
</script>

<style lang="scss" scoped>
.arrt-eidt-wrapper {
  display: flex;
  .arrt-eidt-l {
    width: 108px;
  }
  .arrt-eidt-r {
    flex: 1;
  }
}
</style>
