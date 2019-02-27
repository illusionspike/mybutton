<template>
  <v-app>
    <v-toolbar app class="indigo darken-4 white--text">
      <v-toolbar-title class="headline text-uppercase">
        <v-icon large color="red1" id="iconToolbar">fas fa-briefcase-medical</v-icon>
      
        <span class="red--text">Emergency</span>
        <span class="font-weight-light"> Button</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
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
        <Alert/>
      </v-flex>
    </v-layout>
  </v-container>
  </v-app>
  
</template>

<script>
// eslint-disable-next-line <Drawer/>
/* eslint-disable */
  import Alert from '../components/Alert'
  import Drawer from '../components/Drawer'
  export default {
    name: "Home",
    components: {
      Alert,
      Drawer
    }
  }
</script>

<style scoped>
#iconToolbar{
  padding-right: 20px;
}
</style>
