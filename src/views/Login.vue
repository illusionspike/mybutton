<template>
 <v-app id="inspire">
    <v-content>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Login</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form v-model='valid' ref='form' lazy-validation>
                  <v-text-field 
                  prepend-icon="person" 
                  v-model="username" 
                  name="login" 
                  label="Login"
                  :rules="usernameRules"
                  type="text"
                  required
                  ></v-text-field>
                  <v-text-field 
                  prepend-icon="lock" 
                  v-model="password" 
                  name="password" 
                  label="Password" 
                  id="password" 
                  type="password"
                  :rules="passwordRules"
                  required
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn @click='submit' color="primary">Login</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
// eslint-disable-next-line
/* eslint-disable */
import axios from "axios";
export default {
  data() {
    return {
      valid: true,
      username: "",
      password: "",
      usernameRules: [v => !!v || "Name is required"],
      passwordRules: [v => !!v || "Password is required"],
      items: [
        { title: "Home", icon: "dashboard", route: "/" },
        { title: "Configuration", icon: "question_answer", route: "/about" }
      ],
      right: null
    };
  },
  methods: {
    async submit() {
      this.$refs.form.validate()
      return axios({
        method: "post",
        data: {
          username: this.username,
          password: this.password
        },
        url: "http://localhost:8081/branchs/login",
        headers: {
          "Content-Type": "application/json"
        }
      })
        .then(() => {
          this.$swal("Great!", "You are ready to start!", "success");
          bus.$emit("refreshUser");
          this.$router.push({ name: "Home" });
        })
        .catch(error => {
          const message = error.response.data.message;
          this.$swal("Oh oo!", `${message}`, "error");
          this.$router.push({ name: "Login" });
        });
    }
  }
};
</script>
