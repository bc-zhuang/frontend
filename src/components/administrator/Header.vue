<template>
    <header>
        <div>
            <h1 style="margin-top: -10px;color: #425049;font-size:30px; ">不动产预约后台管理系统</h1>
        </div>
        <div>
            <div class="opt-wrapper">
                <el-dropdown :hide-on-click="false">
                    <div class="demo-basic--circle">
                        <div class="block">
                            <el-avatar :size="40" :src="avatar" :class="['avatar-info']"></el-avatar>
                        </div>
                    </div>
                    <el-dropdown-menu slot="dropdown" style="margin-top:-30px;margin-left: -40px;">
                        <el-dropdown-item><i class="el-icon-info"></i>个人中心</el-dropdown-item>
                        <el-dropdown-item @click.native="logout"><i class="el-icon-switch-button"></i>退出登录</el-dropdown-item>
                    </el-dropdown-menu>
                </el-dropdown>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            avatar: require('@/assets/images/Administrator_Avatar.jpg')
        }
    },
    methods:{
        logout(){
            this.$axios.post('/logout',this.loginForm).then(res=>{
                console.log(res)
                //清理数据
                this.$store.commit('resetState');
                //跳转到登录路由
                this.$router.push({path:'/Home/Main'})
            });
        }

    }
}
</script>

<style scoped>
header {
    margin-top: auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: #fff;
}
/*设定头像图片样式*/
.avatar-info {
    margin-top: 10px;
    margin-right: 40px;
    cursor: pointer;
}
</style>
