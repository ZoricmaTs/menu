<template>
  <div class="page">
    <input type="checkbox" id="nav-toggle" hidden />

    <nav class="nav">
      <label for="nav-toggle" class="nav-toggle" onclick></label>
      <ul class="nav__list">
        <li
          class="nav__item"
          v-for="(item, index) in menu"
          :key="item.id"
          v-bind:class="{active: index == active}"
        >
          <a class="nav__link" href="#" @click="active = index">
            <div class="nav__title">
              {{item.menu_title}}
              <p class="nav__subtitle">{{item.menu_subtitle}} &nbsp;</p>
            </div>
            <div class="nav__arrow material-icons">navigate_next</div>
          </a>
        </li>
      </ul>
    </nav>

    <section class="body-block">
      <div class="screen-size">
        <div class="screen-size__block">
          <span class="screen-size__vers material-icons">stay_current_portrait</span>
          <span class="screen-size__vers material-icons">tablet_mac</span>
          <span class="screen-size__vers material-icons">tv</span>
        </div>
        <div class="screen-size__line">&nbsp;</div>
      </div>

      <Content v-bind:item="menu[active].content" />
    </section>
    <router-view />
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/icon?family=Material+Icons");
@import url("https://fonts.googleapis.com/css?family=Open+Sans:400,
  300&subset=latin,
  cyrillic");
@import "@/assets/scss/style.scss";
* {
  margin: 0;
  padding: 0;
}
body {
  font-family: "Raleway", sans-serif;
  font-style: normal;
  font-weight: 400;
  -webkit-animation: bugfix infinite 1s;
}
.nav__item.active {
  background-color: #141413;
}
</style>

<script>
import axios from "axios";
import Content from "@/components/Content.vue";
export default {
  components: {
    Content
  },
  data() {
    return {
      baseUrl: process.env.VUE_APP_BASE_URL,
      active: 1,
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
            image_url:
              "https://img5.goodfon.ru/wallpaper/nbig/b/3b/window-desk-watches-notebook-smartphone-headphones.jpg",
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
            image_url:
              "https://img2.goodfon.ru/wallpaper/nbig/9/44/notebook-tablet-mouse-desk.jpg",
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
            image_url:
              "https://img5.goodfon.ru/wallpaper/nbig/4/65/wallpaper-computer-room-desktop.jpg",
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
          id: 5,
          menu_title: "Thank you",
          menu_subtitle: "",
          content: {}
        }
      ]
    };
  },
  methods: {
    fetchData() {
      axios.get(this.baseUrl + "file.json").then(response => {
        console.log(response);
      });
    }
  },
  mounted() {
    this.fetchData();
  },
  computed: {
    total() {
      return this.menu.length;
    }
  }
};
</script>