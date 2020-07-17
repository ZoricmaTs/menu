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
          <a class="nav__link" href="#" @click="selectMenu(index)">
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

      <Content v-bind:item="activeContent" />
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
      active: 0,
      activeContent: {},
      openContent: false,
      menu: []
    };
  },
  methods: {
    fetchData() {
      axios.get("http://localhost:8080/file.json").then(response => {
        this.menu = response.data.menu;
        if (response.data.menu.length > 0) {
          let menu = this.menu[0];

          if (typeof menu.content !== "undefined") {
            this.activeContent = menu.content;
          }
        }
      });
    },
    selectMenu(index) {
      let menu = this.menu[index];
      if (typeof menu.content !== "undefined") {
        this.activeContent = menu.content;
      } else {
        this.activeContent = {};
      }

      this.active = index;
    }
  },

  created() {
    this.fetchData();
  },
  computed: {
    total() {
      return this.menu.length;
    }
  }
};
</script>