<template>
  <div id="home">
    <v-row>
      <v-col align="center" justify="center">
        <v-card
            class="mx-auto"
            max-width="740"
        >
          <v-card-text><h1>Menu</h1></v-card-text>
          <v-form>
            <v-container fluid>
              <v-row class="login">
                <v-col
                    cols="12"
                    sm="6"
                >
                  <v-btn
                      @click="quiz">
                    Get my custom skin care plan
                  </v-btn>
                </v-col>
              </v-row>
              <v-row class="login">
                <v-col
                    cols="12"
                    sm="6"
                >
                  <v-btn
                      @click="info">
                    View my profile
                  </v-btn>
                </v-col>
              </v-row>
              <v-row class="login">
                <v-col
                    cols="12"
                    sm="6"
                >
                  <v-btn
                      @click="settings">
                    Account Settings
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
  name: 'Home',
  components: {}
  ,

  methods: {
    quiz() {
      const self = this;
      self.$router.push('/quiz');
    },
    info() {
      const self = this;
      self.$router.push('/profile');
    },
    settings() {
      const self = this;
      self.$router.push('/settings');
    }
  }
}
</script>
