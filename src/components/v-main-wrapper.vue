<template>
  <div class="v-main-wrapper">
  <div class="form">
    <div class="container">
      <vReviews/>
      <vAuth/>
    </div>
  </div>
  </div>
</template>

<script>
import vAuth from './v-auth.vue';
import vReviews from './v-reviews.vue';
export default {
  name: 'v-main-wrapper', 
  components: {
    vReviews,
    vAuth
  }
}
</script>

<style>
.container {
    display: flex;
    justify-content: space-between;
    margin: auto;
    width: 785px;
}

.form__container {
    display: flex;
    width: 410px;
}

</style>