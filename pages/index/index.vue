<template>
  <view class="content">
    <view class="status_bar">
      <text class="leftIcon" @click="record">历史记录</text>
      uni-push
      <text class="rightIcon" @click="add">添加</text>
    </view>
    <view class="demoList">
      <view class="demoItem" v-for="item in [1, 2, 3, 4]" :key="item.id">
        {{ item }}
      </view>
      <view class="demoItem">123123</view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {};
  },
  onLoad() {
    uni.showToast({
      title: "数据库",
      duration: 2000,
    });
  },
  methods: {
    record() {
      console.log("record");
      plus.sqlite.openDatabase({
        name: "record",
        path: "_doc/push.db",
        success: function (e) {
          console.log("openDatabase success!");
          uni.showToast({
            title: "数据库",
            duration: 2000,
          });
        },
        fail: function (e) {
          console.log("openDatabase failed: " + JSON.stringify(e));
          uni.showToast({
            title: "数据库已经打开",
            duration: 2000,
          });
        },
      });
    },
    add() {
      console.log("add");
    },
  },
};
</script>

<style lang="less" scoped>
.content {
  display: flex;
  flex-direction: column;
  background-color: #f1f1f1;
  height: 100vh;
}
.status_bar {
  padding-top: var(--status-bar-height);
  width: 100%;
  height: 80rpx;
  line-height: 80rpx;
  text-align: center;
  background-color: #ffffff;
  border-bottom: 1rpx solid #c8c7cc;
  position: relative;
  .leftIcon {
    position: absolute;
    left: 20rpx;
  }
  .rightIcon {
    position: absolute;
    right: 20rpx;
  }
}
.demoList {
  padding: 20rpx;
  .demoItem {
    padding: 10rpx;
    padding-top: 20rpx;
    background-color: #fff;
    border-radius: 10rpx;
    margin-bottom: 20rpx;
  }
}
</style>
