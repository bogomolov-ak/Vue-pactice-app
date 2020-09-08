<template>
  <v-app>
    <v-card color="grey lighten-4" flat height="200px" tile>
      <v-navigation-drawer app temporary v-model="drawer">
        <v-card class="mx-auto" max-width="300" tile>
          <v-list dense>
            <v-subheader>REPORTS</v-subheader>
            <v-list-item-group v-for="link of links" :key="link.title" :to="link.url" color="primary">
              <v-list-item>
                <v-list-item-icon>
                  <v-icon>{{ link.icon }}</v-icon>
                </v-list-item-icon>
                <v-list-item-content>
                  <v-list-item-title v-text="link.title"></v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list-item-group>
          </v-list>
        </v-card>
      </v-navigation-drawer>

      <v-toolbar dense dark color="primary">
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title>Add application</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn v-for="link in links" :key="link.title" flat color="primary">
          <v-icon>{{ link.icon }}</v-icon>{{ link.title }}
        </v-btn>

      </v-toolbar>
    </v-card>
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'App',

  components: {},

  data: () => ({
    drawer: false,
    links: [
      {
        title: 'Login',
        icon: 'mdi-lock',
        url: '/login'
      },
      {
        title: 'Registration',
        icon: 'mdi-face',
        url: '/registration'
      },
      {
        title: 'Orders',
        icon: 'mdi-star',
        url: '/orders'
      },
      {
        title: 'New add',
        icon: 'mdi-bookmark-plus',
        url: '/new'
      },
      {
        title: 'My adds',
        icon: 'mdi-border-all',
        url: '/list'
      }
    ]
  })
})
</script>
