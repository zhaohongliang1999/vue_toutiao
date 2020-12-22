<template>
  <div class="update-name">
    <!-- 导航栏 -->
    <van-nav-bar
      title="编辑昵称"
      left-text="取消"
      right-text="确定"
      @click-left="$emit('close')"
    />
    <!-- /导航栏 -->
    <!-- 输入框 -->
    <div style="field-wrap">
      <van-field
        v-model="message"
        rows="2"
        autosize
        type="textarea"
        maxlength="7"
        placeholder="请输入新昵称"
        show-word-limit
      />
    </div>
    <!-- /输入框 -->
  </div>
</template>

<script>
export default {
  name: "UpdateName",
  data () {
    return {
      message : ''
    }
  }
};
</script>

<style lang="less">
.field-wrap {
  padding: 10px;
}
</style>
