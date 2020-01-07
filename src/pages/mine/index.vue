<template>
  <div>
  <view class="userinfo">
    <view class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <open-data type="userNickName"></open-data>
    </view>  
    <i-panel center title="~~美味佳肴，值得推荐~~">
      <i-input :value="name" @change="changeName($event)" title="菜肴名称" autofocus placeholder="请输入菜名" maxlength="20" />
      <i-input :value="taste" @change="changeTaste($event)" title="来源地址" placeholder="请输入来源地址" maxlength="20" />
      <i-input :value="remark" @change="changeRemark($event)" title="主要食材" placeholder="请输入主要食材" maxlength="50" />
      <i-button @click="handleClick" type="error" shape="circle" size="small" >推 荐 佳 肴</i-button>
    </i-panel>
    
  </div>
</template>

<script>
export default {
  data () {
    return {
      name:"",
      taste:"",
      remark:""
    }
  },

  methods: {
    changeName (event) {
      this.name = event.mp.detail.detail.value
    },
    changeTaste (event) {
      this.taste = event.mp.detail.detail.value
    },
    changeRemark(event) {
      this.remark = event.mp.detail.detail.value
    },
    
    handleClick () {
      if (this.name && this.taste && this.remark) {
        wx.showToast({
          title: '推荐了' + this.name,
          icon: 'warning',
          duration: 2000
        })
        // TODO:将推荐数据提交到云数据库
      } else {
        wx.showToast({
          title: '信息不完整',
          icon: 'none',
          duration: 2000
        })
      }
    }
  },

  created () {
  }
}
</script>

<style scoped>
.userinfo {
  position: relative;
  width: 750rpx;
  height: 320rpx;
  color: #666;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  overflow: hidden;
  display: block;
  width: 160rpx;
  height: 160rpx;
  margin: 20rpx;
  margin-top: 50rpx;
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
}

.tips {
  padding: 20pt;
  font-size: 10pt;
  color:lightblue;
}
</style>
