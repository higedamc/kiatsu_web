<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="clipped"
      fixed
      app
      class="hidden-md-and-up"
    >
      <v-list>
        <v-list-tile
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-tile-action>
            <v-layout justify-center>
              <font-awesome-icon :icon="item.icon" style="font-size: 30px;" />
            </v-layout>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title" />
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar color="primary" fixed app dark>
      <v-toolbar-side-icon class="hidden-md-and-up" @click="drawer = !drawer" />
      <v-toolbar-title to="/" v-text="title" />
      <v-spacer />
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn v-for="(item, i) in items" :key="i" :to="item.to" flat>
          {{ item.title }}
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <v-container grid-list-md>
        <transition name="fade">
          <nuxt />
        </transition>
      </v-container>
    </v-content>
    <v-footer :fixed="true" color="primary" dark app>
      <v-layout justify-center>
        <span>&copy; 2022 Kohei Otani. All Rights Reserved.</span>
      </v-layout>
    </v-footer>
  </v-app>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

export default {
  components: {
    FontAwesomeIcon
  },
  data() {
    return {
      clipped: false,
      drawer: false,
      items: [
        { icon: ['fas', 'envelope'], title: 'Contact', to: '/contact' }
      ],
      title: "KIATSU"
    }
  }
}
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
