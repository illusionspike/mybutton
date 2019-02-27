<template>
  <v-navigation-drawer 
  class="white--text"
  permanent
  width=270
  >
    <v-toolbar flat> 
      <v-list>
        <v-list-tile>
          <v-list-tile-title class="title">
            Menu
          </v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-toolbar>

    <v-divider></v-divider>

    <v-list dense class="pt-0">
      <v-list-tile
        v-for="item in items"
        :key="item.title"
        router :to="item.route"
         active-class="indigo1--text"
      >
        <v-list-tile-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-tile-action>

        <v-list-tile-content>
          <v-list-tile-title>{{ item.title }}</v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
  export default {
    data () {
      return {
        code: '#1A237E',
        items: [
          { title: 'Home', icon: 'fas fa-home' , route: '/' },
          { title: 'Configuration', icon: 'fas fa-tools', route: '/config' },
          { title: 'Logout', icon: 'fas fa-sign-out-alt', route: '/login' }
        ],
        right: null
      }
    }
  }
</script>