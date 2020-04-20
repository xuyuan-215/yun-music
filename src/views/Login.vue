<template>
  <div class="bg">
    <mu-container>
      <mu-form ref="form" :model="validateForm" class="mu-demo-form">
        <mu-container>
          <mu-text-field v-model="value13" label="UserName" label-float help-text="用户名为6-12长度的字符" icon="账号"></mu-text-field><br />
          <mu-text-field v-model="value14" label="Password" label-float error-text="请输入密码" icon="密码"></mu-text-field><br />
        </mu-container>
        <mu-form-item prop="isAgree" :rules="argeeRules">
          <mu-checkbox label="同意用户协议" v-model="validateForm.isAgree"></mu-checkbox>
        </mu-form-item>
        <mu-form-item>
          <mu-button color="primary" @click="submit">提交</mu-button>
          <mu-button @click="clear">重置</mu-button>
        </mu-form-item>
      </mu-form>
      <mu-dialog title="Dialog" width="360" :open.sync="openSimple">
        登录成功
        <mu-button slot="actions" flat color="primary" @click="closeSimpleDialog">Close</mu-button>
      </mu-dialog>
    </mu-container>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
    return {
      usernameRules: [
        { validate: (val) => !!val, message: '必须填写用户名' },
        { validate: (val) => val.length >= 3, message: '用户名长度大于3' }
      ],
      passwordRules: [
        { validate: (val) => !!val, message: '必须填写密码' },
        { validate: (val) => val.length >= 3 && val.length <= 10, message: '密码长度大于3小于10' }
      ],
      argeeRules: [{ validate: (val) => !!val, message: '必须同意用户协议' }],
      validateForm: {
        username: '',
        password: '',
        isAgree: false
      },
      menuList: [],
      openSimple: false
    }
  },
  components: {},
  created() {},
  mounted() {},
  methods: {
    openSimpleDialog() {
      this.openSimple = true
    },
    closeSimpleDialog() {
      this.openSimple = false
    },
    submit() {
      this.$refs.form.validate().then((result) => {
        console.log('form valid: ', result)
        //模拟后端接口数据
        let user = {
          userId: '2000100193',
          username: 'taoranran',
          userRole: 'admin',
          avatar:
            'https://public-cdn-oss.mosoteach.cn/avatar/2018/62/3322dd0ba40a79be5369ac01656581fc.jpg?v=1581858255&x-oss-process=style/s200x200'
        }
        this.menuList = [
          { title: 'Dashboard', icon: 'mdi-view-dashboard', url: '/dashboard', subMenus: [] },
          {
            title: '音乐管理',
            icon: 'mdi-music',
            url: '',
            subMenus: [
              {
                title: '歌单管理',
                icon: 'mdi-domain',
                url: '/music-list',
                permissions: []
              },
              {
                title: '歌曲管理',
                icon: 'mdi-text',
                url: '/music',
                permissions: ['music:add', 'music:edit', 'music:delete']
              }
            ]
          },
          { title: 'About', icon: 'mdi-help-box', url: '/about', subMenus: [] }
        ]
        localStorage.setItem('token', 'EcIHTAWoGrmMVvTu2LPvuL-siq6hAfieVeehl-HTe_M')
        localStorage.setItem('user', JSON.stringify(user))
        localStorage.setItem('menuList', JSON.stringify(this.menuList))
        this.$store.commit('setToken', 'EcIHTAWoGrmMVvTu2LPvuL-siq6hAfieVeehl-HTe_M')
        this.$store.commit('setUser', user)
        this.$store.commit('setMenuList', this.menuList)
        this.$router.push('/')
        this.openSimpleDialog()
      })
    },
    clear() {
      this.$refs.form.clear()
      this.validateForm = {
        username: '',
        password: '',
        isAgree: false
      }
    }
  },
  computed: {}
}
</script>

<style scoped lang="scss">
.bg {
  background: -webkit-linear-gradient(to bottom, #7bc6cc, #be93c5);
  background: linear-gradient(to bottom, #7bc6cc, #be93c5); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  background-image: url('../assets/images/5.jpg');
  opacity: 0.8;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.mu-demo-form {
  max-width: 500px;
  margin-left: 300px;
  background-color: #fff;
  border-radius: 10px;
  padding: 10px;
}
</style>
