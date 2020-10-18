<template>
  <div id="login">
    <v-row>
      <v-col align="center" justify="center">
    <v-card
        class="mx-auto"
        max-width="380"
    >
      <v-card-text><h1>Welcome</h1></v-card-text>
    <v-form>
      <v-container fluid>
        <v-row class="login">
          <v-col class="login"
            cols="12"
            sm="6"
          >
            <v-text-field
              v-model="input.username"
              label="Email"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-row class="login">
          <v-col class="login"
            cols="12"
            sm="6"
          >
            <v-text-field
              v-model="input.password"
              type="password"
              label="Password"
              ></v-text-field>
          </v-col>
        </v-row>
        <v-row class="login">
          <v-col
            cols="12"
            sm="6"
          >
            <v-btn
                @click="login">
              Login
            </v-btn>
          </v-col>
          <v-col>
            <v-btn
                @click="register">
              Register
            </v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
    </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<style>
  .login {
    text-align: center;
    justify-content: center;
  }
</style>

<script>
export default {
  name: 'Login',
  data() {
    return {
      input: {
        username: "",
        password: ""
      },
    }
  },
  methods: {
    login() {
      const self = this;

      fetch('https://localhost:44372/login', {
        method: 'post',
        headers: new Headers({'content-type': 'application/json'}),
        body: JSON.stringify(this.input)
      }).then(function (response) {
        if (!response.ok) {
          throw Error(response.statusText)
        }
        self.$router.push('/home');
      }).catch(function(error) {
        console.log(error);
      });
    },

    register() {
      const self = this;
        self.$router.push('/register');
      }
    }
}
</script>