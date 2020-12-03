<template>
<div class="v-reviews">
<div class="form__container">
                <div class="form__reviews">

                    <button class="reviews__arr" id="reviews__arrow--left">
                        <svg class="reviews__arr-img">
                            <use xlink:href="#arr"></use>
                        </svg>
                    </button>

                    <div class="reviews__comma">
                        <img src="assets/img/quotes.png" />
                    </div>

                    <div class="reviews" id="reviews">
                        
                        <div class="reviews__item">
                            
                            <div class="reviews__text">Мамси, спасибо Вам огромное за такие красивые платья!
                                Сегодня получила новенькое платьице. Боже мой как оно мне понравилось...
                                какое красивое.. и ведь платье совсем не дорогое! Спасибо</div>
                            <div class="reviews__person">
                                <img class="reviews__person-photo" src="assets/img/person.png" />
                                <div class="reviews__person-info">
                                    <div class="reviews__person-name">Алла г. Москва</div>
                                    <div class="reviews__person-date">с нами 4 года, 3 месяца, 65 заказов</div>
                                </div>
                            </div>
                        </div>

                        <div class="reviews__item splite__slide">
                            <div class="reviews__text">Все что я заказывала на сайте все просто супер!
                                Вещи отличные. Заказала сыну куртку steen age очень довольна, она офигенная,
                                с кучей карманов, даже с термометром)))) и скидка была 70%.</div>
                            <div class="reviews__person">
                                <img class="reviews__person-photo" src="assets/img/person2.png" />
                                <div class="reviews__person-info">
                                    <div class="reviews__person-name">Мария г. Барнаул</div>
                                    <div class="reviews__person-date">с нами 2 года, 4 месяца, 32 заказа</div>
                                </div>
                            </div>
                        </div>

                        <div class="reviews__item splite__slide">
                            <div class="reviews__text">Добрый день, Мамси! Спасибо за заказ номер 1703226!
                                Уютное постельное белье дарит нам прекрасные сны! А валеночки для лапочки-дочки
                                просто чудо! Теплые, мягкие! СПАСИБО, МАМСИ, ЧТО ТЫ ЕСТЬ!</div>
                            <div class="reviews__person">
                                <img class="reviews__person-photo" src="assets/img/person3.png" />
                                <div class="reviews__person-info">
                                    <div class="reviews__person-name">Елена г. Санкт-Петербург</div>
                                    <div class="reviews__person-date">с нами 5 лет, 1 месяц, 535 заказов</div>
                                </div>
                            </div>
                        </div>

                        <div class="reviews__item splite__slide">
                            <div class="reviews__text">Здравствуйте, Mamsy! Вчера получила первый заказ! Дочке зимний
                                комплект, себе платье! Мне очень понравилось! Качество супер! Размер в точку! И цена
                                радует! Буду заказывать ещё! Спасибо!</div>
                            <div class="reviews__person">
                                <img class="reviews__person-photo" src="assets/img/person4.png" />
                                <div class="reviews__person-info">
                                    <div class="reviews__person-name">Ольга г. Новосибирск</div>
                                    <div class="reviews__person-date">с нами 1 месяц, 1 заказ</div>
                                </div>
                            </div>
                        </div>

                        <div class="reviews__item splite__slide">
                            <div class="reviews__text">Только что получила свой большой заказ. Накопила
                                баллов и потратила на 50% скидку. Коробка еле прошла в дверь. Вещи
                                подошли отлично. Мамси, огромное спасибо! Не знаю, что бы я без Вас делала.</div>
                            <div class="reviews__person">
                                <img class="reviews__person-photo" src="assets/img/person5.png" />
                                <div class="reviews__person-info">
                                    <div class="reviews__person-name">Ольга г. Казань</div>
                                    <div class="reviews__person-date">с нами 4 года, 3 месяца, 455 заказов</div>
                                </div>
                            </div>
                        </div>
                        
                    </div>

                    <button class="reviews__arr" id="reviews__arrow--right">
                        <svg class="reviews__arr-img">
                            <use xlink:href="#arr"></use>
                        </svg>
                    </button>
                </div>
            </div>
            </div>
</template>

<script>
export default {
  name: 'v-reviews'
}
</script>

<style>
.form {

    &__reviews {
        width: 100%;
        position: relative;
        
        background-repeat: no-repeat;
        height: 583px;

        display: flex;
        justify-content: space-between;
        align-items: center;
    }
}

.reviews {
    position: relative;
    width: 380px;
    margin: 0 auto -280px;

    &__item {
        width: inherit;
        padding: 30px;
        background-color: #ffffff;
    }

    &__comma {
        position: absolute;
        top: 51%;
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
</style>