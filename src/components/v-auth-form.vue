<template>
  <div class="v-auth-form">
    <form
      id="auth"
      class="auth__form"
      @submit.prevent="checkForm"
      action="something"
      method="post"
      novalidate="true"
    >
      <div class="auth__input">
        <input
          @input="checkEmail"
          class="auth__form-user"
          placeholder="Введите email"
          type="email"
          name="email"
          id="email"
          v-model="email"
        />
        <p class="fail__comm" v-if="errorsEmail.length">
          <span class="fail__comment">{{ errorsEmail[0] }}</span>
        </p>
      </div>

      <div class="auth__input">
        <input
          @input="checkPassword"
          class="auth__form-user"
          placeholder="Придумайте пароль"
          type="text"
          name="password"
          id="password"
          v-model="password"
        />
        <p class="fail__comm" v-if="errorsPass.length">
          <span class="fail__comment-password">{{ errorsPass[0] }}</span>
        </p>
      </div>
      <div class="auth__input" v-if="showReg" >
            <input class="auth__form-user" placeholder="Введите Ваше имя">
      </div>
      <button type="submit" class="auth__form-btn" v-if="showAuth" >Войти</button>
      <button type="submit" class="auth__form-btn" v-if="showReg" >Вступить в клуб</button>
    </form>
  </div>
</template>

<!--<form class="auth__form">
                    <div class="auth__input">
                        <input class="auth__form-user  fail" placeholder="Введите email"></input>
                        <span class="fail__comment">Введите email</span>
                    </div>

                    <div class="auth__input">
                        <input class="auth__form-user" placeholder="Придумайте пароль"></input>
                        <span class="fail__comment  hide">Ваш пароль</span>
                    </div>
                    
                    <div class="auth__input">
                        <input class="auth__form-user" placeholder="Введите Ваше имя"></input>
                        <span class="fail__comment  hide">Ваше имя</span>
                    </div>
                    
                    <button class="auth__form-btn">Вступить в клуб</button>
                </form>
-->
<script>
export default {
  name: "v-auth-form",
  props: ["showReg", "showAuth"],
  data() {
    return {
      errorsEmail: [],
      errorsPass: [],
      email: null,
      password: null,
    };
  },
  methods: {
    checkForm: function (e) {
      this.errorsEmail = [];
      this.errorsPass = [];

      if (!this.email) {
        this.errorsEmail.push("Введите email");
      } else if (!this.validEmail(this.email)) {
        this.errorsEmail.push("Введите валидный E-Mail");
      }
      if (!this.password) {
        this.errorsPass.push("Введите пароль");
      }
    },
    validEmail: function (email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    checkEmail: function (e) {
      this.errorsEmail = [];

      if (!this.email) {
        this.errorsEmail.push("Введите email");
      } else if (!this.validEmail(this.email)) {
        this.errorsEmail.push("Введите валидный E-Mail");
      }
    },
    checkPassword: function (e) {
      this.errorsPass = [];
      if (this.password.trim().length == 0) {
        this.errorsPass.push("Введите пароль");
      } else if (this.password.trim().length < 6) {
        this.errorsPass.push("Пароль должен содержать минимум 6 символов");
      }

      /*if(this.password.trim().length < 6 && this.password.trim().length != 0) {
          this.errorsPass.push('Пароль должен содержать минимум 6 символов');
      } else if(this.password.trim().length == 0) {
          this.errorsPass.push('Введите пароль');
      }*/
    },
  },
};
</script>