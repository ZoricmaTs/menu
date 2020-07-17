<template>
  <section class="content">
    <div class="content__block-img">
      <img class="content__img" :src="item.image_url" v-if="item.image_url" />
    </div>
    <div class="content__block-text">
      <header class="content__header" v-if="item.header">{{item.header}}</header>
      <p class="content__short-text" v-if="item.short_text">{{item.short_text}}</p>
      <span class="content__full-text" v-if="item.full_text">{{item.full_text}}</span>
      <button class="content__btn" v-if="item.full_text_btn_title">{{ item.full_text_btn_title }}</button>
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
  },
  methods: {}
};
</script>

<style lang="scss" scoped>
</style>