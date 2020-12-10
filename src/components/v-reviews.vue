<template>
  <div class="v-reviews" v-on:click="greet">
    <div class="form__container">
      <div v-bind:class="showReg ? 'form__reviewsReg' : 'form__reviews'" >
        <div v-bind:class="showReg ? 'reviews__commaReg' : 'reviews__comma'">
          <img src="../assets/img/quotes.png" />
        </div>

        <vReviewsSlider v-bind:showReg="showReg" />

        <div class="reviews__scores" v-if="showReg">
          <img src="../assets/img/250.png" />
        </div>

        <a href="#" class="reviews__detail">Подробнее о клубе мамси</a>
      </div>
    </div>
  </div>
</template>

<script>
import vReviewsSlider from "./v-reviews-slider.vue";
export default {
  name: "v-reviews",
  props: ["showReg"],
  components: {
    vReviewsSlider,
  },

  methods: {
    greet: function(e) {
      this.$emit('greet')
    },
  }
};
</script>

<style lang="scss">
.form {
  &__reviewsReg {
    width: 100%;
    position: relative;

    background-image: url("../assets/img/backReg.jpg");
    background-repeat: no-repeat;
    height: 583px;

    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__reviews {
    width: 100%;
    position: relative;

    background-image: url("../assets/img/back.jpg");
    background-repeat: no-repeat;
    height: 583px;

    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}

.reviewsReg {
  position: relative;
  width: 380px;
  margin: 0 auto -130px;
}

.reviews {
  position: relative;
  width: 380px;
  margin: 0 auto -280px;

  &__detail {
    position: absolute;
    bottom: -4%;
    left: 50%;
    transform: translateX(-50%);
    color: white;
    font-size: 11px;

    &:hover {
      color: #e71e6c;
    }
  }

  &__item {
    width: 84%;
    padding: 30px;
    background-color: #ffffff;
  }

  &__scores {
    position: absolute;
    bottom: 2%;
    left: 50%;
    transform: translateX(-50%);
  }

  &__comma {
    position: absolute;
    top: 51%;
    left: 4%;
    z-index: 10;
  }

  &__commaReg {
    position: absolute;
    top: 38%;
    left: 4%;
    z-index: 10;
  }

  &__text {
    color: #666;
    font-size: 14px;
    font-style: italic;
    line-height: 1.5;
    margin-bottom: 20px;
  }

  &__person {
    position: relative;
    display: flex;

    &-photo {
      width: 53px;
      height: 53px;
    }

    &-info {
      position: absolute;
      top: 0;
      left: 0;
      transform: translateY(50%) translateX(35%);
    }

    &-name {
      font-size: 14px;
    }

    &-date {
      font-size: 12px;
      color: #666;
    }
  }

  &__arr {
    position: absolute;
    bottom: 25%;
    left: 8%;
    transform: rotate(180deg);
    border: none;
    background: none;
    z-index: 10;
    width: 18px;
    height: 18px;
    outline: none;

    &:last-child {
      left: 88%;
      transform: rotate(0);
    }

    &-img {
      width: 18px;
      height: 18px;
      fill: #e71e6c;
    }
  }
}

@media (max-width: 755px) {
  .v-reviews {
    display: none;
  }
}
</style>