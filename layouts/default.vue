<template>
  <div class='wrapper'>
    <v-navigation-drawer
      temporary
      v-model="drawer"
      absolute
      class="blue lighten-3" dark
    >
      <v-list class="pa-1">
        <v-list-tile avatar>
          <v-list-tile-avatar>
            <img src="https://randomuser.me/api/portraits/men/85.jpg" >
          </v-list-tile-avatar>
          <v-list-tile-content>
            <v-list-tile-title>John Leider</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
      <v-list class="pt-0" dense>
        <v-divider></v-divider>
        <v-list-tile v-for="item in items" :key="item.title">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <header>
      <v-toolbar light>
        <v-toolbar-side-icon @click.stop="drawer = !drawer" class="hidden-md-and-up"></v-toolbar-side-icon>
        <v-toolbar-title class="nav-title">Значки ССО</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <nuxt-link to="/"><v-btn class="nav-link" flat>Главная</v-btn></nuxt-link>
          <nuxt-link to="/galery"><v-btn class="nav-link" flat>Галерея</v-btn></nuxt-link>
          <nuxt-link to="/users"><v-btn class="nav-link" flat>Пользователи</v-btn></nuxt-link>
          <nuxt-link to="/contact"><v-btn class="nav-link" flat>Связаться</v-btn></nuxt-link>
        </v-toolbar-items>
      </v-toolbar>
    </header>
    <div class="container">
      <nuxt/>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      drawer: false,
    }
  }
}
</script>

<style>
html
{
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  background-color: #fffcf0;
  color: #252c41;
}
*, *:before, *:after
{
  box-sizing: border-box;
  margin: 0;
}
li {
  list-style: none
}
a {
  text-decoration: none;
}
.wrapper {
  max-width: 960px;
  margin: 0 auto;
  background-color: #d6ecfa;
}

.container
{
  margin: 0 auto;
  min-height: 100vh;
}
section {
  display: flex;
  flex-flow: column;
  align-items: center;
}
.section-content {
  width: 100%;
}

.section-title {
  margin: 15px 0 30px 0;
  position: relative;
  display: inline-block;
  line-height: 1.6;
  width: 400px;
  /*text-align: center;*/
}
.section-title::after, .section-title::before {
  content: "";
  position: absolute;
  height: 4px;
  width: 100%;
  background-color: #f1404b;
  transition: 0.4s all ease;
  transform-origin: 0% 50%;
}
.section-title::after {
  transform: rotate(180deg) translateX(-400px);
}
.section-title h1 {
  text-align: center;
}
section:hover .section-title::after {
  height: 1px;
  width: 0;
}
section:hover .section-title::before {
  width: 0;
  height: 1px;
}
nav ul {
  display: flex;
}
.nav-link {
  color:#F8FAFF;
  font-weight: bold;
  margin: 0px;
  height: initial;
}

header a {
  display: flex
}
header {
  background-color: #a3daff;
}
.nav-title {
  font-size: 30px;
  font-weight: bold;
}
.input-group--selection-controls__ripple::after {
  background-color: #fafafa;
}
.input-group__details {
  display: none;
}


  </style>
