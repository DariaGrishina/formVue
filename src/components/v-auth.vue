<template>
<div class="v-auth">
  <div class="auth">
                <div class="auth__logo">
                    <img src="assets/img/logo.svg"/>
                </div>
                <div class="auth__text">
                    <span class="auth__text-pink">11 024 159</span> женщин со всей<br> России уже перестали переплачивать<br> за <span class="auth__text-pink">качественные товары</span> вместе с Mamsy
                </div>
                <div class="auth__check check hideCheckFirst">
                    <div class="check__block">
                        <div class="check__block-mark">
                            <svg class="mark">
                                <use xlink:href="#check"></use>
                            </svg>
                        </div>
                        <div class="check__block-text">Скидки до 70% на товары для всей семьи</div>
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
                <form id="auth" class="auth__form" @submit.prevent="checkForm" action="something" method="post" novalidate="true">
                    <div class="auth__input">
                        <input @input="checkEmail" class="auth__form-user" placeholder="Введите email"  type="email" name="email" id="email" v-model="email"></input>
                        <p v-if="errorsEmail.length">
                            <span class="fail__comment">{{ errorsEmail[0] }}</span>
                        </p>
                    </div>

                    <div class="auth__input">
                        <input @input="checkPassword" class="auth__form-user" placeholder="Придумайте пароль" type="text" name="password" id="password" v-model="password"></input>
                        <p v-if="errorsPass.length">
                            <span class="fail__comment-password">{{ errorsPass[0] }}</span>
                        </p>
                    </div>
                    <button type="submit" class="auth__form-btn">Войти</button>
                </form>
                <a href="#" class="auth__forget">Забыли пароль?</a>
                <div class="auth__enter">
                    Ещё не с нами? 
                    <a href="#" class="auth__enter-register">Вступить в клуб</a>
                </div>
                <div class="auth__arrow">
                    <img src="assets/img/arrow.png" />
                </div>
                <div class="auth__logo hideCheck">
                    <img class="auth__logo-icon" src="assets/img/vk.svg" alt="">
                    <img class="auth__logo-icon" src="assets/img/ok.svg" alt="">
                    <img class="auth__logo-icon" src="assets/img/face.svg" alt="">
                    <img class="auth__logo-icon" src="assets/img/google.svg" alt="">
                </div>
                <div class="auth__check check hideCheck">
                    <div class="check__block">
                        <div class="check__block-mark">
                            <svg class="mark">
                                <use xlink:href="#check"></use>
                            </svg>
                        </div>
                        <div class="check__block-text">Скидки до 70% на товары для всей семьи</div>
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
                <div class="auth__app hideCheck">
                    <div class="auth__app-title">Мобильное приложение</div>
                    <div class="auth__app-apps">
                        <img class="auth__app-store hideCheck" src="assets/img/appStore.png" alt="">
                        <img class="auth__app-store hideCheck" src="assets/img/googlePlay.png" alt="">
                    </div>
                    <a href="" class="auth__app-description hideCheck">О клубе Mamsy</a>
                </div>
            </div>
            </div>
</template>

<script>
export default {
  name: 'v-auth',
  data: {
      errorsEmail: [],
      errorsPass: [],
      email: null,
      password: null
    },
    methods: {
      checkForm: function (e) {  
        this.errorsEmail = [];
        this.errorsPass = [];
  
        if (!this.email) {
            this.errorsEmail.push('Введите email');
          } else if (!this.validEmail(this.email)) {
            this.errorsEmail.push('Введите валидный E-Mail');
        }
        if (!this.password) {
          this.errorsPass.push('Введите пароль');
        }
      },
      validEmail: function (email) {
        var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return re.test(email);
      },
      checkEmail: function(e) {
        this.errorsEmail = [];

        if (!this.email) {
            this.errorsEmail.push('Введите email');
          } else if(!this.validEmail(this.email)) {
            this.errorsEmail.push('Введите валидный E-Mail');
        }

      },
      checkPassword: function(e) {
        this.errorsPass = [];
        if(this.password.trim().length == 0) {
          this.errorsPass.push('Введите пароль');
        } else if(this.password.trim().length < 6) {
          this.errorsPass.push('Пароль должен содержать минимум 6 символов');
        }


        /*if(this.password.trim().length < 6 && this.password.trim().length != 0) {
            this.errorsPass.push('Пароль должен содержать минимум 6 символов');
        } else if(this.password.trim().length == 0) {
            this.errorsPass.push('Введите пароль');
        }*/

      }
    }
}

</script>