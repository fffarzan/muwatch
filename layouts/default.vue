<template>
  <v-app dark>
    <!-- navbar -->
    <v-app-bar :clipped-left="clipped" fixed tag="nav" app>
      <v-toolbar-title class="yellow--text text--accent-4" v-text="title" />
      <v-spacer />
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
    </v-app-bar>

    <!-- nav drawer -->
    <v-navigation-drawer
      v-model="drawer"
      :clipped="clipped"
      fixed
      right
      tag="section"
      app
    >
      <p class="navdrawer-heading text-center yellow--text text--accent-4 my-5">
        Mu Watch
      </p>
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- main -->
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <!-- footer -->
    <v-footer :absolute="false" tag="footer" app>
      <span class="mx-auto yellow--text text--accent-4">
        fffarzan / &copy; {{ new Date().getFullYear() }}
      </span>
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

@Component
export default class DefaultLayout extends Vue {
  title = 'Mu Watch';
  drawer = false;
  clipped = false;
  items = [
    {
      icon: 'mdi-home-variant-outline',
      title: 'Home',
      to: '/',
    },
    {
      icon: 'mdi-information-outline',
      title: 'About',
      to: '/about',
    },
  ];
}
</script>

<style scoped>
.navdrawer-heading {
  font-size: 25px;
}
</style>
