<template>
  <div>
    <nav role="navigation">
      <div id="menuToggle">
        <input type="checkbox" />

        <span></span>
        <span></span>
        <span></span>
        <ul class="nav__list" id="menu">
          <li class="nav__item" v-for="item in menu" :key="item.id">
            <a
              class="nav__link"
              href="#"
              @click="openContent = !openContent"
              v-for="(item, index) in menu"
              :key="item"
              v-show="index === active"
            >
              <div class="nav__title">
                {{item.menu_title}}
                <p class="nav__subtitle">{{item.menu_subtitle}} &nbsp;</p>
              </div>
              <div class="nav__arrow material-icons">navigate_next</div>
            </a>
          </li>
        </ul>
      </div>
    </nav>

    <section class="body-block">
      <div class="screen-size">
        <div class="screen-size__block">
          <span class="screen-size__vers material-icons">stay_current_portrait</span>
          <span class="screen-size__vers material-icons">tablet_mac</span>
          <span class="screen-size__vers material-icons">tv</span>
        </div>
      </div>
      <div class="screen-size__line"></div>
      <Content
        @click="openContent = !openContent"
        v-for="(item, index) in menu"
        :key="item"
        v-show="index === active"
      />
    </section>
    <router-view />
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/icon?family=Material+Icons");
@import "@/assets/scss/style.scss";
* {
  margin: 0;
  padding: 0;
}
body {
  font-family: "Raleway", sans-serif;
  font-style: normal;
  font-weight: 400;
}
</style>

<script>
import Content from "@/components/Content.vue";
export default {
  components: {
    Content
  },
  data() {
    return {
      openContent: false,
      menu: [
        {
          id: 1,
          menu_title: "Main page",
          menu_subtitle: "About us",
          content: {
            header: "Lorem ipsum",
            short_text:
              "Suspendisse fringilla dui nulla, sit amet fermentum nunc consectetur eget.",
            full_text:
              "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            image_url: "/path/to/image/file.png",
            full_text_btn_title: "Learn more"
          }
        },
        {
          id: 2,
          menu_title: "Shop",
          menu_subtitle: "Our products to buy",
          content: {
            header: "Products",
            short_text:
              "Suspendisse fringilla dui nulla, sit amet fermentum nunc consectetur eget. In vitae nulla a est tristique porttitor.",
            full_text:
              "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            image_url: "/path/to/image/file2.png",
            full_text_btn_title: "Get more products"
          }
        },
        {
          id: 3,
          menu_title: "Contacts",
          menu_subtitle: "Call us",
          content: {
            header: "Contacts",
            short_text: "Phone:  8-800-555-3555 \nEmail: some_email@domain.com",
            full_text: "",
            image_url: "/path/to/image/file3.png",
            full_text_btn_title: "Learn more"
          }
        },
        {
          id: 4,
          menu_title: "Thank you",
          menu_subtitle: "",
          content: {
            header: "Thank you",
            short_text: "We will be glad to see you again",
            full_text:
              "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            image_url: "",
            full_text_btn_title: ""
          }
        },
        {
          id: 4,
          menu_title: "Thank you",
          menu_subtitle: "",
          content: {}
        }
      ]
    };
  },
  methods: {
    change(index) {
      this.invert = index < this.active;
      this.active = (index + this.total) % this.total;
    }
  },
  mounted() {},
  computed: {
    total() {
      return this.menu.length;
    }
  }
};
</script>