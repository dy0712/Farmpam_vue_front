<template>
  <div class="LoginForm">
    <section class="section section--login">
      <div class="inner">
        <div class="login-image">
          <img src="../assets/images/farm4.jpg" class="img-fluid" alt="" />
        </div>

        <div class="inner-border">
          <div class="inner-form">
            <img class="logo" src="../assets/images/logo.png" alt="" />

            <form
              ref="loginform"
              method="post"
              @submit.prevent="onLogin"
              class="login--form row g-3"
              action="/farmer/vue/login.do"
            >
              <div class="col-12 input__text">
                <input
                  type="text"
                  class="form-control"
                  id="farmer_email"
                  name="farmer_email"
                  placeholder="이메일"
                  v-model="email"
                />
              </div>

              <div class="col-12 input__text">
                <input
                  type="password"
                  class="form-control"
                  id="farmer_pwd"
                  name="farmer_pwd"
                  placeholder="비밀번호"
                  v-model="password"
                />
              </div>
              <span v-show="isLogin" class="badge bg-primary"
                >로그인 정보가 틀려요 !</span
              >
              <div class="col-12">
                <button type="submit" class="btn btn-primary">로그인</button>
              </div>
              <div class="line">
                <p class="or">또는</p>
              </div>
              <a class="google-login mb-3" href="#">구글 계정으로 로그인</a>
            </form>
            <div class="signup-link">
              <p class="mb-2">계정이 없으신가요?</p>
              <router-link to="/farmersignup">농부로 가입하기</router-link>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "FarmerLogin",
  components: {},
  data() {
    return {
      email: "",
      password: "",
      isLogin: false,
    }
  },
  methods: {
    onLogin() {
      const formdata = new FormData(this.$refs.loginform)

      this.$store
        .dispatch("loginAction", {
          form: formdata,
          num: 1,
        })
        .then((result) => {
          console.log("로그인 요청 결과 : " + result)
          if (result) {
            alert("로그인 성공")
            this.$router.push({ path: "/" })
          } else {
            this.isLogin = true
          }
        })
    },
  },
}
</script>

<style scoped>
html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}

/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}
body {
  line-height: 1;
}
ol,
ul {
  list-style: none;
}
blockquote,
q {
  quotes: none;
}
blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}

.section {
  position: relative;
  padding: 75px 0;
}

.inner {
  width: 100%;
  margin: 0 auto;
  position: relative;
  display: flex;
  justify-content: center;
}

.Login {
  background-color: rgba(var(--b3f, 250, 250, 250), 1);
}

h1 {
  font-size: 32px;
}

.login-image {
  width: 564px;
  height: 800px;
  overflow: hidden;
}

.login-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.inner-border {
  width: 564px;
  border: 1px solid rgba(var(--b6a, 219, 219, 219), 1);
  padding-top: 40px;
  padding-bottom: 40px;
  display: flex;
  background-color: #ffffff;
}

.line {
  display: flex;
  flex-basis: 100%;
  align-items: center;
  color: rgba(0, 0, 0, 0.35);
  font-size: 14px;
  padding: 20px;
}

.line::before {
  content: "";
  flex-grow: 1;
  margin: 0px 20px 0px 100px;
  background: rgba(0, 0, 0, 0.35);
  height: 1px;
  font-size: 0px;
  line-height: 0px;
}

.line::after {
  content: "";
  flex-grow: 1;
  margin: 0px 100px 0px 20px;
  background: rgba(0, 0, 0, 0.35);
  height: 1px;
  font-size: 0px;
  line-height: 0px;
}

.inner-form {
  margin: auto;
  text-align: center;
}

.inner-form h1 {
  padding: 32px;
  text-align: center;
}
w .login--form {
  text-align: center;
}

.login--form a {
  text-decoration: none;
}

.input__text {
  padding: 0px 100px 0px 100px;
}

.signup-link {
  text-align: center;
  border: 1px solid #cecece;
  margin: 0 50px;
  padding: 20px;
}

.signup-link a {
  color: limegreen;
  text-decoration: none;
}

.logo {
  width: 300px;
  height: 140px;
}
</style>
