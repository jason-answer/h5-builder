<template>
  <el-form-item label="图片列表：">
    <div>&nbsp;</div>
    <div>
      <div v-for="(item, index) in tempValue" :key="index" class="attr-edit-wrapper">
        <imageSelect :url.sync="item.url" @change="change" />
        <div class="attr-edit-btn-wrapper">
          <span class="imageSelect-btn" @click="add(index)">
            <i class="el-icon-circle-plus-outline" />
          </span>
          <span v-show="tempValue.length > 1" class="imageSelect-btn error" @click="del(index)">
            <i class="el-icon-remove-outline" />
          </span>
        </div>
      </div>
    </div>
  </el-form-item>
</template>

<script>
import imageSelect from '@client/components/image-select';

export default {
  name: 'attr-qk-imageSrcList',
  components: {
    imageSelect
  },
  props: {
    imageSrcList: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      tempValue: []
    };
  },
  watch: {
    imageSrc() {
      this.initData();
    },
    tempValue() {
      this.change();
    }
  },
  created() {
    this.initData();
  },
  methods: {
    initData() {
      const list = [];
      this.imageSrcList.forEach(item => {
        list.push({ url: item });
      });
      this.tempValue = list;
    },
    getResultImageSrcList() {
      const list = [];
      for (let i = 0, len = this.tempValue.length; i < len; i++) {
        list.push(this.tempValue[i].url);
      }
      return list;
    },
    change() {
      this.$emit('update:imageSrcList', this.getResultImageSrcList());
    },
    add(index) {
      const img = this.tempValue[index];
      this.tempValue.splice(index, 0, { ...img });
    },
    del(index) {
      this.tempValue.splice(index, 1);
    }
  }
};
</script>

<style lang="scss" scoped>
.attr-edit-wrapper {
  display: block;
  width: 100%;
  position: relative;
}

.attr-edit-btn-wrapper {
  position: absolute;
  bottom: 0;
  right: 8px;
  .imageSelect-btn {
    margin-left: 8px;
    font-size: 24px;
    cursor: pointer;
    &:hover {
      color: $primary;
    }
    &.error {
      color: inherit;
      &:hover {
        color: $error;
      }
    }
  }
}
</style>
