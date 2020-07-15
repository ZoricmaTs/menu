<template>
  <section class="content">
    <!-- <img class="content__img" src="./img/file.jpg" /> -->
    <div class="content__block-text">
      <header class="content__header">Drag and drop website builder</header>
      <p class="content__short-text">Make you own website in a few clicks!fdgdfgdfgdg</p>
      <p class="content__full-text">&nbsp;</p>
      <button
        class="content__btn"
        :full_text_btn_title="this.full_text_btn_title"
      >{{ this.full_text_btn_title }}</button>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    header: { type: String },
    short_text: { type: String },
    full_text: { type: String },
    image_url: { type: String }
  },
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
</style>