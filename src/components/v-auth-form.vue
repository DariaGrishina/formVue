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
          <span class="fail__comment">{{ errorsPass[0] }}</span>
        </p>
      </div>
      <div class="auth__input" v-if="isShowReg" >
          <input class="auth__form-user" placeholder="Введите Ваше имя" v-model="name">
      </div>
      <button @click="getDataAuth" type="submit" class="auth__form-btn" v-if="isShowAuth" >Войти</button>
      <button @click="getDataReg" type="submit" class="auth__form-btn" v-if="isShowReg" >Вступить в клуб</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "v-auth-form",
  props: ["isShowReg", "isShowAuth"],
  data() {
    return {
      errorsEmail: [],
      errorsPass: [],
      email: null,
      password: null,
      name: null,
      isDisabled: true
    };
  },
  methods: {
    getDataAuth: function(e) {
      let user = {
        userEmail: this.email,
        userPass: this.password
      }
      console.log(user)
    },
    getDataReg: function(e) {
      let user = {
        userEmail: this.email,
        userPass: this.password,
        userName: this.name
      }
      console.log(user)
    },
    /*disableButton: function(e) {
      if (!this.email || !this.password) {
        console.log('ddd');
        this.isDisabled = true; 
      } else {
        console.log('hhh');
        this.isDisabled = false;
      }
    },*/
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
    },
  },
};
</script>

<style lang="scss">
  .fail {
  position: relative;
  border-color: red;
  margin-bottom: 10px;

  &__comm {
    position: relative;
    margin: 0;
    width: 100%;
    padding: 5px 0;
  }

  &__comment {
    position: absolute;
    bottom: -5px;
    right: 0;
    font-size: 11px;
    font-weight: 300;
    color: red;

    &-password {
      position: absolute;
      bottom: 36%;
      right: 11.5%;
      font-size: 11px;
      font-weight: 300;
      color: red;

      .auth__input {
        margin-bottom: 13px;
      }
    }
  }
}

  .auth {
    &__form {
    display: flex;
    flex-direction: column;
    text-align: center;
    margin: 3px 0;

    &-user {
      padding: 13px 15px;
      border-radius: 3px;
      border: 1px solid rgb(230, 227, 227);
      outline: none;
      box-sizing: border-box;
      width: 100%;

      &::placeholder {
        font-size: 13px;
        font-weight: 300;
        color: rgb(187, 186, 186);
      }
    }

    &-btn {
      margin: 12px 40px 0 40px;
      height: 45px;
      background-color: #e71e6c;
      border: none;
      border-radius: 3px;
      color: #fff;
      font-size: 20px;
      cursor: pointer;

      &:focus {
        outline: none;
      }

      &:hover {
        background-color: #a5496c;
      }
    }
  }

  &__input {
    padding: 0px 40px 0 40px;
    margin-bottom: 10px;
    box-sizing: border-box;
  }

  @media (max-width: 755px) {
    .auth {
      &__form {
        &-btn {
          margin: 0 25px;
        }

        &-user {
          padding: 13px 15px;
          width: 100%;
        }
      }

      &__input {
        padding: 0 25px;
        margin-bottom: 7px;
      }
    }

    .fail__comment {
      top: 2px;
      right: 0;
      font-size: 10px;
    }
  }
  }
</style>