<template>
  <div v-bind:class="showReg ? 'reviewsReg' : 'reviews'" id="reviews">
    <splide :options="options" @splide:moved="moved">
      <splide-slide v-for="(slide, id) in slides" :key="id">
        <div class="reviews__item">
          <div class="reviews__text">{{ slide.text }}</div>
          <div class="reviews__person">
            <img class="reviews__person-photo" v-bind:src="slide.img"  />
            <div class="reviews__person-info">
              <div class="reviews__person-name">{{ slide.name }}</div>
              <div class="reviews__person-date">{{ slide.date }}</div>
            </div>
          </div>
        </div>
      </splide-slide>
    </splide>
  </div>
</template>

<script>
import { Splide, SplideSlide } from "@splidejs/vue-splide";
import "@splidejs/splide/dist/css/themes/splide-default.min.css";

export default {
  name: "v-reviews-slider",
  props: ["showReg"],
  data() {
    return {
      options: {
        rewind: true,
        gap: "1rem",
      },
      slides: [
        {
          text: `Мамси, спасибо Вам огромное за такие красивые платья!
            Сегодня получила новенькое платьице. Боже мой как оно мне понравилось...
            какое красивое.. и ведь платье совсем не дорогое! Спасибо`,
          img: "assets/img/person.png",
          name: "Алла г. Москва",
          date: "с нами 4 года, 3 месяца, 65 заказов",
        },
        {
          text: `Все что я заказывала на сайте все просто супер!
            Вещи отличные. Заказала сыну куртку steen age очень довольна, она офигенная,
            с кучей карманов, даже с термометром)))) и скидка была 70%`,
          img: "../assets/img/person2.png",
          name: "Мария г. Барнаул",
          date: "с нами 2 года, 4 месяца, 32 заказа",
        },
        {
          text: `Добрый день, Мамси! Спасибо за заказ номер 1703226!
            Уютное постельное белье дарит нам прекрасные сны! А валеночки для лапочки-дочки
            просто чудо! Теплые, мягкие! СПАСИБО, МАМСИ, ЧТО ТЫ ЕСТЬ!`,
          img: "../assets/img/person3.png",
          name: "Елена г. Санкт-Петербург",
          date: "с нами 5 лет, 1 месяц, 535 заказов",
        },
        {
          text: `Здравствуйте, Mamsy! Вчера получила первый заказ! Дочке зимний
            комплект, себе платье! Мне очень понравилось! Качество супер! Размер в точку! И цена
            радует! Буду заказывать ещё! Спасибо!`,
          img: "../assets/img/person4.png",
          name: "Ольга г. Новосибирск",
          date: "с нами 1 месяц, 1 заказ",
        },
        {
          text: `Только что получила свой большой заказ. Накопила
            баллов и потратила на 50% скидку. Коробка еле прошла в дверь. Вещи
            подошли отлично. Мамси, огромное спасибо! Не знаю, что бы я без Вас делала.`,
          img: "../assets/img/person5.png",
          name: "Ольга г. Казань",
          date: "с нами 4 года, 3 месяца, 455 заказов",
        },
      ],
    };
  },
  methods: {
    moved(splide, newIndex) {
      console.log("moved", newIndex);
    },
  },
  components: {
    Splide,
    SplideSlide,
  },
};
</script>

<style lang="scss">
.splide__arrow {
  position: absolute;
  bottom: 25%;
  border: none;
  background: none;
  z-index: 10;
  width: 18px;
  height: 18px;
  outline: none;

  &--next {
    left: 93%;
    transform: rotate(0deg);
  }

  &--prev {
    left: 2%;
    transform: rotate(0deg);
  }

  svg{
    height: 18px;
    width: 18px;
    fill: #e71e6c;
  }
}

.splide__pagination__page {
  background: black;
}

.splide__pagination__page.is-active {
  background: #e71e6c;
}

.splide__pagination__page.is-active {
  transform: scale(1);
}
</style>