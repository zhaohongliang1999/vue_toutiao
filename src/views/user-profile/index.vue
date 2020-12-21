<template>
  <div class="user-profile">
    <!-- 导航栏 -->
    <van-nav-bar
    class="page-nav-bar"
    title="个人信息"
    left-arrow 
    @click-left="$router.back()" />
    <!-- /导航栏 -->
      <!-- 个人信息 -->
    <van-cell title="头像" is-link>
      <van-image
        class="avatar"
        fit="cover"
        round
        :src="user.photo"
      />
    </van-cell>
    <van-cell title="昵称" 
    :value="user.name" 
    is-link 
    @click="isShowUpdateName = true"
    />
    <van-cell title="性别" 
    :value="user.gender === 0 ? '男' : '女' " 
    is-link />
    <van-cell title="生日" :value="user.birthday" is-link />
    <!-- /个人信息 -->
    <!-- 编辑昵称弹层 -->
    <van-popup
    v-model="isShowUpdateName"
    style="height: 100%"
    position="bottom">
      编辑昵称
    </van-popup>
    <!-- 编辑昵称弹层 -->
  </div>
</template>

<script>
import { getUserProfile } from '@/api/user'
export default {
  name : 'UserProfile',
  data () {
    return {
      user : {}, // 个人信息
      isShowUpdateName : false // 控制编辑名称弹层
    }
  },

  created () {
     this.loadUserProfile()
  },

  methods: {
     async loadUserProfile() {
       try {
         const { data } = await getUserProfile()
         this.user = data.data
       } catch (err) {
         this.$toast('数据获取失败')
       }
     }
  }
}
</script>

<style scoped lang='less'>
 .avatar {
   width: 60px;
   height: 60px;
 }
</style>
