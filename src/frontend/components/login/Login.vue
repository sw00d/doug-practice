<template>
  <v-container fluid fill-height>
    <v-layout align-center justify-center>
      <v-flex md4>
        <v-card>
          <v-toolbar class="toolbar elevation-0">
            <v-toolbar-title>Login Form</v-toolbar-title>
            <div class="dash"></div>
          </v-toolbar>
          <v-form @submit.prevent="login" novalidate>
            <v-card-text>
              <v-alert outlined type="error" v-if="errors.non_field_errors || errors.detail">
                <ul>
                  <li v-for="(error, i) in errors.non_field_errors" :key="i">{{ error }}</li>
                </ul>
                {{ errors.detail }}
              </v-alert>

              <v-text-field
                v-model="form.email"
                label="User Name"
                name="user"
                :error="!!errors.email"
                :error-messages="errors.userName"
                prepend-icon="person"
                type="text"></v-text-field>
              <v-text-field
                v-model="form.password"
                label="Password"
                name="password"
                :error="!!errors.password"
                :error-messages="errors.password"
                prepend-icon="fingerprint"
                ref="password"
                onfocus="this.select()"
                type="password"></v-text-field>
            </v-card-text>

            <v-card-actions class="login-buttons">
              <v-btn 
                type="submit" 
                class="green--text" 
                v-on:click="guestHome"  
                to="/guestHome">
                <strong
                >
                  guest</strong>
              </v-btn>
              <v-btn 
                type="submit" 
                id="login-button" 
                v-on:click="asset-calculator"
                to="/asset-calculator"
                class="primary white--text"
                depressed
                width="135"
              >
                Login
              </v-btn>
              <v-spacer></v-spacer>
              <v-switch
                color="primary"
                v-model="switch1"
                inset
                label="Remember Me"
                 >
               
              </v-switch>
            </v-card-actions>   
          </v-form>
        </v-card>
            <div id="spacer">
                <NuxtLink to="/password-reset" class="white--text">
                Forgot Password
                </NuxtLink>
            </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  
  auth: false,
  data() {
    return {
      errors: {},
      form: {
        email: '',
        password: '',
        guest: ""
      },
      remember_me: true,
      switch1: true,
    }
  },
  methods: {
    async login() {
      try {
        await this.$auth.login({ data: this.form })

        this.$nuxt.$router.push('/')

        // IMPORTANT! Do our initializing! (from our auth plugin)
        this.$auth.ctx.app.project_initialize()

        // TODO: We need to make a good client side initialization spot...
        // Connect to websocket and start receiving store commits from backend
        this.$store.dispatch('realtime/start_listening')

        this.errors = {}
      } catch (e) {
        if (e.response) {
          this.errors = e.response.data
        } else {
          console.error(e)
        }

        // focus on in the input to easily re-enter password
        this.$refs.password.focus()
      }
    }
  }
}
</script>

<style scoped>

.toolbar {
  border-bottom: gray;
  border-style: solid;
  border-width: thin;
  
}
  .display-1{
    font-size: 1rem;
}

  #spacer {
    margin: 5% 0 0 0;
  }

.dash {
  background-color: var(--v-primary-base);
  height: 14%;
  width: 50px;
  margin: 60px 0 0 -101px;
}

@media only screen and (max-width: 415px) {
  .login-buttons {
    display: inline;
    margin: 0 0 0 10px;
  }
}
</style>

