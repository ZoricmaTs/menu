<template>
  <section class="content">
    <img class="content__img" :src="image_url" />
    <div class="content__block-text">
      <header class="content__header">{{item.header}}</header>
      <p class="content__short-text">{{item.short_text}}</p>
      <p class="content__full-text">{{item.full_text}}</p>
      <button class="content__btn">{{ item.full_text_btn_title }}</button>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    item: Object
  },
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
</style>