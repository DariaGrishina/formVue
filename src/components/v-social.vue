<template>
  <div v-bind:class="showReg ? 'socialReg' : 'social'">
    <div class="auth__quickEnter1">Быстрый вход</div>
    <div class="auth__icons">
      <a v-for="(item,key) in social"
         :key="key"
         :href="item.link"
          class="auth__icons-link"
      >
        <img :src="item.img"
             alt=""
             class="auth__icons-icon"
        >
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'v-social',
  props: ['showReg'],
  data() {
    return {
      social: [
        {
          link:'#',
          img: require('@/assets/img/vk.svg')
        },
        {
          link:'#',
          img: require('@/assets/img/ok.svg')
        },
        {
          link:'#',
          img: require('@/assets/img/face.svg')
        },
        {
          link:'#',
          img: require('@/assets/img/google.svg')
        },
      ]
    }
  }
}
</script>

<style lang="scss">
.social {
  position: absolute;
  bottom: -34px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  left: 0;

  @media (max-width: 755px) {
    position: static;
    margin-top: -22px;
  }
}

.socialReg {
  position: absolute;
  bottom: -34px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  left: 0;

  @media (max-width: 755px) {
    position: static;
    margin-top: -22px;
    text-align: left;
  }
}

.auth {
    &__quickEnter1 {
        color: white;
        font-size: 11px;
        margin-right: 10px;

        @media (max-width: 755px) {
            display: none;
        }
    }

    &__icons {
        &-icon {
            display: block !important;
        }

        &-link {
            display: inline-block;
            margin: 0 4px;

            &:last-child img {
                margin-right: 0;
            }
        }
    }
}
</style>