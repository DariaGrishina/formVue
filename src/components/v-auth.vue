<template>
  <div class="v-auth">
    <div class="auth">
      <div class="auth__logo">
        <img src="../assets/img/logo.svg" />
      </div>
      <div class="auth__text">
        <span class="auth__text-pink">11 024 159</span> женщин со всей<br />
        России уже перестали переплачивать<br />
        за <span class="auth__text-pink">качественные товары</span> вместе с
        Mamsy
      </div>
      <div class="auth__check check hideCheckFirst">
        <div class="check__block">
          <div class="check__block-mark">
            <svg class="mark">
              <use xlink:href="#check"></use>
            </svg>
          </div>
          <div class="check__block-text">
            Скидки до 70% на товары для всей семьи
          </div>
        </div>
        <div class="check__block">
          <div class="check__block-mark">
            <svg class="mark">
              <use xlink:href="#check"></use>
            </svg>
          </div>
          <div class="check__block-text">Топ-бренды со всего мира</div>
        </div>
        <div class="check__block">
          <div class="check__block-mark">
            <svg class="mark">
              <use xlink:href="#check"></use>
            </svg>
          </div>
          <div class="check__block-text">Тысячи новых товаров каждый день</div>
        </div>
      </div>

      <vAuthForm v-bind:isShowReg="isShowReg" v-bind:isShowAuth="isShowAuth"/>

      <div class="auth__policy" v-if="isShowReg">
            Нажимая на кнопку, я соглашаюсь с
           <a href="#" class="auth__policy-doc">условиями</a>
      </div>
      <div v-bind:class="isShowReg ? 'auth__enterReg' : 'auth__enter'" v-if="isShowReg">
            Зарегистрированы?
            <a @click="showFunc" href="#" class="auth__enter-register">Вход здесь</a>
      </div>

      <a href="#" class="auth__forget" v-if="isShowAuth">Забыли пароль?</a>
      <div class="auth__enter" v-if="isShowAuth">
        Ещё не с нами?
        <a @click="showFunc" href="#" class="auth__enter-register">Вступить в клуб</a>
      </div>
      <div v-bind:class="isShowReg ? 'auth__arrowReg' : 'auth__arrow'" >
        <img src="../assets/img/arrow.png" />
      </div>
      <vSocial v-bind:isShowReg="isShowReg"/>
      
      <div class="auth__check check hideCheck">
        <div class="check__block">
          <div class="check__block-mark">
            <svg class="mark">
              <use xlink:href="#check"></use>
            </svg>
          </div>
          <div class="check__block-text">
            Скидки до 70% на товары для всей семьи
          </div>
        </div>
        <div class="check__block">
          <div class="check__block-mark">
            <svg class="mark">
              <use xlink:href="#check"></use>
            </svg>
          </div>
          <div class="check__block-text">Топ-бренды со всего мира</div>
        </div>
        <div class="check__block">
          <div class="check__block-mark">
            <svg class="mark">
              <use xlink:href="#check"></use>
            </svg>
          </div>
          <div class="check__block-text">Тысячи новых товаров каждый день</div>
        </div>
      </div>
      <div class="auth__app">
        <div class="auth__app-title hideCheck">Мобильное приложение</div>
        <div class="auth__app-apps">
          <img
            class="auth__app-store hideCheck"
            src="../assets/img/appStore.png"
            alt=""
          />
          <img
            class="auth__app-store hideCheck"
            src="../assets/img/googlePlay.png"
            alt=""
          />
        </div>
        <a href="" class="auth__app-description hideCheck">О клубе Mamsy</a>
      </div>
    </div>
  </div>
</template>

<script>
import vAuthForm from "./v-auth-form.vue";
import vSocial from "./v-social.vue";
export default {
  name: "v-auth",
  props: ["isShowReg", "isShowAuth"],
  components: {
    vAuthForm,
    vSocial
  },
  data() {
    return {
      errorsEmail: [],
      errorsPass: [],
      email: null,
      password: null
    };
  },
  methods: {
    showFunc: function(e) {
      this.$emit('changeForm');
    }
  },
};
</script>

<style lang="scss">
.v-auth {
    position: relative;
    background-color: white;
    @media (max-width: 755px) {
      width: 100%;
    }
}

.auth {
  width: 375px;
  text-align: center;
  background-color: white;

  &__quickEnter {
    position: absolute;
    bottom: -10.5%;
    left: 13%;
    color: white;
    font-size: 11px;
  }

  &__quickEnterReg {
    position: absolute;
    bottom: -14%;
    left: 13%;
    color: white;
    font-size: 11px;
  }

  &__close {
    position: absolute;
    top: 10px;
    right: 10px;
    border: none;
    outline: none;
    background: none;
    z-index: 1;

    &-icon {
      width: 13px;
      height: 13px;
    }
  }

  &__logo {
    margin: 15px 0;
  }

  &__text {
    margin: 0 30px;
    font-size: 14px;
    line-height: 20px;
    color: #666;

    &-pink {
      color: #e71e6c;
    }
  }

  /*&__input {
    padding: 0px 40px 0 40px;
    margin-bottom: 10px;
    box-sizing: border-box;
  }*/

  /*&__form {
    display: flex;
    flex-direction: column;
    text-align: center;
    margin: 3px 0;

    &-user {
      padding: 13px 121px 13px 15px;
      border-radius: 3px;
      border: 1px solid rgb(230, 227, 227);
      outline: none;

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
  }*/

  &__forget {
    color: #666;
  }

  &__enterReg {
    position: absolute;
    bottom: 37px;
    left: 57px;
    font-style: italic;

    &-register {
      color: #e71e6c;
    }
  }

  &__enter {
    position: absolute;
    bottom: 37px;
    left: 57px;
    font-style: italic;

    &-register {
      color: #e71e6c;
    }
  }

  &__arrowReg {
    position: absolute;
    bottom: 20px;
    left: -44px;
  }

  &__arrow {
    position: absolute;
    bottom: 20px;
    left: -44px;
  }

  &__policy {
    font-size: 12px;
    font-weight: 300;
    color: rgb(187, 186, 186);

    &-doc {
      color: rgb(187, 186, 186);
    }
  }

  &__icons {
    &-icon {
      display: none;
    }
  }

  &__iconsDeskReg {
    position: absolute;
    display: flex;
    bottom: -17%;
    left: 50%;
    transform: translateX(-50%);

    &:last-child {
      margin-right: 0;
    }
    &-icon {
        display: inline;
        margin: 8px 8px 8px 0;
        height: 25px;
        width: 25px;

        &:last-child {
          margin-right: 0;
        }
    }
  }

  &__iconsDesk {
    position: absolute;
    display: flex;
    bottom: -13.5%;
    left: 50%;
    transform: translateX(-50%);

    &:last-child {
      margin-right: 0;
    }
    &-icon {
        display: inline;
        margin: 8px 8px 8px 0;
        height: 25px;
        width: 25px;

        &:last-child {
          margin-right: 0;
        }
    }
  }
}

.mark {
  width: 18px;
  height: 18px;
  fill: #fdc3d9;
}

.check {
  margin-top: 20px;

  &__block {
    position: relative;
    display: flex;
    margin-bottom: 12px;

    &-mark {
      position: absolute;
      top: 0;
      left: 0;
      margin-left: 40px;
      width: 18px;
      height: 18px;
    }

    &-text {
      margin-left: 65px;
      font-size: 14px;
      font-style: italic;
      color: #666;
    }
  }
}

/*.fail {
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
    bottom: -2px;
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
}*/

.hide {
  display: none;
}

.hideCheck {
  display: none;
}

@media (max-width: 755px) {
  .form__container {
    display: none;
  }

  .hideCheck {
    display: block;
  }

  .hideCheckFirst {
    display: none;
  }

  .check {
    position: relative;
    margin-top: 20px;

    &__block {
      &-text {
        margin-left: 45px;
      }

      &-mark {
        margin-left: 20px;
      }
    }

    &::after {
      content: "";
      position: absolute;
      bottom: -35px;
      left: 0;
      width: 100%;
      height: 1px;
      background-color: #eeeff5;
    }
  }

  /*.fail__comment {
    top: 2px;
    right: 0;
  }*/

  .auth {
    max-width: 340px;
    width: 100%;

    &__close {
      right: 20px;
      top: 20px;
    }

    &__arrowReg {
      display: none;
    }

    &__arrow {
      display: none;
    }

    &__logo {
      margin: 20px 0 0;
    }

    &__forget {
      display: block;
      margin-top: 30px;
    }

    &__enterReg {
      position: relative;
      margin-top: 60px;
      text-align: left;
      width: 243px;
    }

    /*&__input {
      padding: 0 32px;
      margin-bottom: 7px;
    }*/

    /*&__form {
      &-btn {
        margin: 0 32px 28px;
      }

      &-user {
        padding: 13px 0 13px 10px;
        width: 96%;
      }
    }*/

    &__enter {
      position: relative;
      margin-top: 63px;
      text-align: left;
      width: 266px;
    }

    &__quickEnter {
      display: none;
    }

    &__iconsDesk {
      display: none;
    }

    &__icons {
      display: flex;
      justify-content: space-between;
      width: 220px;

      &-icon {
        position: relative;
        display: inline;
        margin: 15px 15px 15px 0;
        height: 40px;
        width: 40px;

        &:last-child {
          margin-right: 0;
        }
      }
    }

    &__app {
      &-title {
        font-style: italic;
        color: gray;
        font-size: 16px;
        margin-top: 70px;
      }

      &-store {
        width: 130px;
        height: auto;
      }

      &-apps {
        margin: 20px 0;
        display: flex;
        justify-content: center;
      }

      &-store {
        &:first-child {
          margin-right: 3px;
        }
      }

      &-description {
        font-size: 16px;
        color: gray;
        margin-bottom: 20px;
      }
    }
  }
}
</style>