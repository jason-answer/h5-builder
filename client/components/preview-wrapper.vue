<template>
  <div class="components-preview">
    <div class="setting-bg" />
    <div class="left-panel">
      <!-- <div class="iframe-wrapper" :style="{width: $config.canvasH5Width + 'px', height: $config.canvasH5Height + 'px'}">
      </div> -->
      <div class="marvel-device iphone-x">
        <div class="notch">
          <div class="camera" />
          <div class="speaker" />
        </div>
        <div class="top-bar" />
        <div class="sleep" />
        <div class="bottom-bar" />
        <div class="volume" />
        <div class="overflow">
          <div class="shadow shadow--tr" />
          <div class="shadow shadow--tl" />
          <div class="shadow shadow--br" />
          <div class="shadow shadow--bl" />
        </div>
        <div class="inner-shadow" />
        <div class="screen">
          <iframe :src="$config.baseURL + '/page/view/' + pageId" frameborder="0" style="background-color:transparent;width: 100%; height: 100%; margin-top: 44px;" />
          <div class="x-bottom-bar">
            <div class="strip" />
          </div>
        </div>
      </div>
    </div>
    <div class="right-panel">
      <slot />
    </div>
    <span class="cloase-btn" @click="closePreview">
      <i class="el-icon-close" />
    </span>
  </div>
</template>

<script>
export default {
  name: 'preview-page',
  props: {
    pageId: String
  },
  data() {
    return {};
  },
  created() {},
  methods: {
    closePreview() {
      this.$emit('closePreview', false);
    }
  }
};
</script>

<style lang="scss" scoped>
.components-preview-inner {
  width: 100%;
}

.setting-bg {
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.8);
  z-index: 1042;
}
.left-panel {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 640px;
  z-index: 1050;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;

  .x-bottom-bar {
    position: absolute;
    bottom: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;

    .strip {
      width: 160px;
      background-color: #4a4949;
      border-radius: 8px;
      height: 8px;
    }
  }
}
.right-panel {
  position: fixed;
  width: 640px;
  top: 0;
  right: 0;
  bottom: 0;
  z-index: 1050;
  background-color: #fff;
  overflow-y: auto;
  color: #333;
}
.iframe-wrapper {
  position: absolute;
  left: 50%;
  top: 50%;
  margin-left: -185px;
  margin-top: -334px;
  background: white;
}
.cloase-btn {
  position: fixed;
  top: 8px;
  right: 20px;
  font-size: 28px;
  color: #7f8593;
  -webkit-transition: all 0.28s;
  transition: all 0.28s;
  z-index: 1060;
  cursor: pointer;
  &:hover {
    color: $primary;
  }
}
</style>
