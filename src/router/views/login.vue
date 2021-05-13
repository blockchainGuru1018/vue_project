<script>
import Layout from '@layouts/auth.vue'
import { authMethods } from '@state/helpers'
import appConfig from '@src/app.config'

export default {
  page: {
    title: 'Log in',
    meta: [{ name: 'description', content: `Log in to ${appConfig.title}` }],
  },
  components: { Layout },
  data() {
    return {
      username: '',
      password: '',
      authError: null,
      tryingToLogIn: false,
    }
  },
  computed: {
    placeholders() {
      return process.env.NODE_ENV === 'production'
        ? {}
        : {
            username: '请输入您的用户名',
            password: '请输入密码',
          }
    },
  },
  methods: {
    ...authMethods,
    // Try to log the user in with the username
    // and password they provided.
    tryToLogIn() {
      this.tryingToLogIn = true
      // Reset the authError if it existed.
      this.authError = null
      return this.logIn({
        username: this.username,
        password: this.password,
      })
        .then((token) => {
          this.tryingToLogIn = false

          // Redirect to the originally requested page, or to the home page
          this.$router.push(this.$route.query.redirectFrom || { name: 'home' })
        })
        .catch((error) => {
          this.tryingToLogIn = false
          this.authError = error
        })
    },
  },
}
</script>

<template>
  <Layout>
    <form :class="$style.outform" @submit.prevent="tryToLogIn">
      <div :class="$style.images">
        <img
          src="http://iot.flsiot.com:202/pub/images/%E7%99%BB%E5%BD%95/u359.svg"
        />
        <img
          src="http://iot.flsiot.com:202/pub/images/%E7%99%BB%E5%BD%95/u360.svg"
        />
        <img
          src="http://iot.flsiot.com:202/pub/images/%E7%99%BB%E5%BD%95/u357.svg"
        />
        <img
          src="http://iot.flsiot.com:202/pub/images/%E7%99%BB%E5%BD%95/u358.svg"
        />
        <img
          src="http://iot.flsiot.com:202/pub/images/%E7%99%BB%E5%BD%95/u361.svg"
        />
      </div>
      <div :class="$style.inform" @submit.prevent="tryToLogIn">
        <img style="transform: rotate(180deg);top: 0px; position: relative;" src="http://iot.flsiot.com:202/pub/images/%E7%99%BB%E5%BD%95/u355.svg">
        <p style="top: -52px; position: relative;text-decoration:none; font-size: 18px">WELCOME</p>
        <div style="top: -45px;position: relative;">
          <p style="font-size: 28px; font-family: 'Arial Black Oblique',serif;">无人值守场站管理平台</p>
          <div :class="$style.buttongroup">
            <BaseInputText
                v-model="username"
                name="username"
                :placeholder="placeholders.username"
            />
            <BaseInputText
                v-model="password"
                name="password"
                type="password"
                :placeholder="placeholders.password"
            />
            <div :class="$style.detail">
              <div style="display: flex;align-items: center;">
                <input
                    id="jack"
                    v-model="checkedNames"
                    type="checkbox"
                    value="Jack"
                />
                <label for="jack">记住我的登录状态</label>
              </div>
              <a :class="$style.link" href="#foo">忘记密码？</a>
            </div>
            <div>
              <BaseButton
                  :disabled="tryingToLogIn"
                  :class="$style.button"
                  type="submit"
              >
                <BaseIcon v-if="tryingToLogIn" name="sync" spin />
                <span v-else>
              登录
            </span>
              </BaseButton>
              <p v-if="authError">
                There was an error logging in to your account.
              </p>
            </div>
          </div>
        </div>
      </div>
    </form>
  </Layout>
</template>

<style lang="scss" module>

.outform {
  display: flex;
  align-items: center;
  width: 600px;
  margin: auto;
  color: white;
  text-align: center;
}
.images {
  display: grid;
  margin-right: 50px;
  img {
    width: 100px;
    height: 70px;
    margin-top: 20px;
    margin-right: auto;
  }
  img:first-child {
    width: 120px;
    height: 100px;
    margin-right: auto;
  }
}
.inform {
  width: 400px;
  text-align: center;
  border-radius: 5px;
  font-size: 13px;
  background-image: url('http://iot.flsiot.com:202/pub/images/%E7%99%BB%E5%BD%95/u354.svg');
}
.buttongroup {
  width: 236px;
  margin: auto;
  input {
    height: 34px;
    padding: 3px 2px 3px 40px;
    font-family: 'Helvetica Normal', 'Helvetica';
    font-weight: 400;
    font-style: normal;
    font-size: 12px;
    border-style: solid;
    border-color: rgba(121, 121, 121, 1);
    border-radius: 3px
  }
}
.detail {
  display: flex;
  width: 100%;
  input {
    width: unset;
    height: unset;
  }
  label {
    padding-left: 10px;
  }
}

.link {
  margin-left: auto;
  color: white;
  text-decoration: none;
}
.button {
  width: 60%;
  padding: 5px;
  margin-top: 20px;
  background-color: rgba(25, 158, 216, 1);
  border-radius: 5px;
  font-size: 13px;
}
</style>
