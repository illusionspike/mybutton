<template>
  <v-app>
    <v-toolbar app class="blue darken-2 white--text">
      <v-toolbar-title class="headline text-uppercase">
        <span>Emergency</span>
        <span class="font-weight-light"> Button</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
      >
        <span class="mr-2 white--text">Supakit Dhamchatsoontree</span>
      </v-btn>
    </v-toolbar>
  <v-container fluid fill-height>
    <v-layout row>
      <v-flex shrink>
        <Drawer/>
      </v-flex>
      <v-flex grow ml-5>
        <Personal/>
      </v-flex>
    </v-layout>
  </v-container>
  </v-app>
  
</template>

<script>
// eslint-disable-next-line <Drawer/>
/* eslint-disable */
  import Personal from '../components/Personal'
  import Drawer from '../components/Drawer'
  export default {
    name: "Config",
    components: {
      Personal,
      Drawer
    }
  }
</script>
