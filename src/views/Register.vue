<template>
  <div id="register">
    <v-row>
      <v-col align="center" justify="center">
        <v-card
            class="mx-auto"
            max-width="380"
        >
          <v-card-text><h1>Account Registration</h1></v-card-text>
          <v-form>
            <v-container fluid>
              <v-row class="login">
                <v-col class="login"
                       cols="12"
                       sm="6"
                >
                  <v-text-field
                      v-model="input.FName"
                      label="First Name"
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
                      v-model="input.LName"
                      label="Last Name"
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
                      v-model="input.PhoneNum"
                      label="Phone Number"
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
                      v-model="input.StreetAddress"
                      label="Street Address"
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
                      v-model="input.City"
                      label="City"
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
                      v-model="input.State"
                      label="State"
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
                      v-model="input.ZIP"
                      label="ZIP Code"
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
                      @click="submit">
                    Submit
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
  name: 'Users',
  data() {
    return {
      input: {
        FName: "",
        LName: "",
        PhoneNum: "",
        StreetAddress: "",
        City: "",
        State: "",
        ZIP: "",
        username: "",
        password: ""
      },
    }
  },
  methods: {

    submit() {
      const self = this;

      fetch('https://localhost:44372/register', {
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
  }
}
</script>