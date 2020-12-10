<template>
  <div class="v-main-wrapper">
    <svg style="display: none">
      <symbol id="check" viewBox="0 0 512 512">
        <g>
          <g>
            <path
              d="M437.019,74.98C388.667,26.629,324.38,0,256,0C187.619,0,123.331,26.629,74.98,74.98C26.628,123.332,0,187.62,0,256
                        s26.628,132.667,74.98,181.019C123.332,485.371,187.619,512,256,512c68.38,0,132.667-26.629,181.019-74.981
                        C485.371,388.667,512,324.38,512,256S485.371,123.333,437.019,74.98z M256,482C131.383,482,30,380.617,30,256S131.383,30,256,30
                        s226,101.383,226,226S380.617,482,256,482z"
            />
          </g>
        </g>
        <g>
          <g>
            <path
              d="M378.305,173.859c-5.857-5.856-15.355-5.856-21.212,0.001L224.634,306.319l-69.727-69.727
                        c-5.857-5.857-15.355-5.857-21.213,0c-5.858,5.857-5.858,15.355,0,21.213l80.333,80.333c2.929,2.929,6.768,4.393,10.606,4.393
                        c3.838,0,7.678-1.465,10.606-4.393l143.066-143.066C384.163,189.215,384.163,179.717,378.305,173.859z"
            />
          </g>
        </g>
      </symbol>

      <symbol id="arr" viewBox="0 0 512.002 512.002">
        <g>
          <path
            d="M388.425,241.951L151.609,5.79c-7.759-7.733-20.321-7.72-28.067,0.04c-7.74,7.759-7.72,20.328,0.04,28.067l222.72,222.105
                            L123.574,478.106c-7.759,7.74-7.779,20.301-0.04,28.061c3.883,3.89,8.97,5.835,14.057,5.835c5.074,0,10.141-1.932,14.017-5.795
                            l236.817-236.155c3.737-3.718,5.834-8.778,5.834-14.05S392.156,245.676,388.425,241.951z"
          />
        </g>
      </symbol>
    </svg>
    <button @click="closeAuth">Вход</button>
    <button @click="closeReg">Регистрация</button>
    <div @changeFormAuth="closeAuth" class="form" v-if="showAuth">
      <div class="container">
        <button @click="close" class="auth__close" >
          <img class="auth__close-icon" src="../assets/img/close.svg" alt="" />
        </button>
        <vReviews />
        <vAuth v-bind:showAuth="showAuth" />
      </div>
    </div>
    <div class="formReg" v-if="showReg">
        <div class="container">
            
          <button @click="close" class="auth__close" >
            <img class="auth__close-icon" src="../assets/img/close.svg" alt="" />
          </button>

          <vReviews v-on:greet="greet" v-bind:showReg="showReg"/>
          <vAuth v-on:changeFormReg="closeReg" v-bind:showReg="showReg" />
        </div>
    </div>
  </div>
</template>

<script>
import vAuth from "./v-auth.vue";
import vReviews from "./v-reviews.vue";

export default {
  name: "v-main-wrapper",
  components: {
    vReviews,
    vAuth,
  },
  data() {
    return {
      showAuth: false,
      showReg: false,
    };
  },
  methods: {
    close: function (e) {
      this.showAuth = false;
      this.showReg = false;
    },
    closeAuth: function (e) {
      this.showAuth = true;
      this.showReg = false;
    },
    closeReg: function () {
      this.showAuth = false;
      this.showReg = true;
    },

    greet: function() {
      alert('ergr');
    }
  },
};
</script>

<style lang="scss">
body {
  background-color: black;
}

.container {
  position: relative;
  display: flex;
  justify-content: center;
  margin: auto;
  max-width: 785px;
  width: 100%;

  @media (max-width: 755px) {
    width: 340px;
  }
}

.form__container {
  display: flex;
  width: 410px;
}
</style>