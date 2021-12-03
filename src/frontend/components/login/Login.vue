<template>
  <v-container fluid fill-height>
    <v-layout align-center justify-center>
      <v-flex md4>
        <v-card>
          <v-toolbar class="display-1-box" >
            <v-toolbar-title class="display-1">Login Form</v-toolbar-title>
          
          <div class="dash"><strong> _</strong></div>
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

            <v-card-actions>
              <v-btn type="submit" style="color: green;" v-on:click="guestHome"  
                to="/guestHome">
                <strong>guest</strong>
              </v-btn>
              <v-btn type="submit" id="login-button" color="rgb(247, 52, 52)" style="color: white;">Login
              </v-btn>
              <v-spacer></v-spacer>
              <v-switch
                color="rgb(252,4,4)"
                v-model="switch1"
                inset
                :label="`Remember Me`">
              </v-switch>
            </v-card-actions>   
          </v-form>
        </v-card>
            <div id="spacer">
                <NuxtLink to="/password-reset" style="color: white">
                Forgot Password?
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
      errors: {
        userName:"please enter a valid user name",
        password:"please enter a valid password"
      },
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
  #login-button {
    color: white;
  }

  #spacer {
    margin: 5% 0 0 0;
  }
.dash {
  color: red;
  font-size: 4em;
  margin: 3% 0 0 -42%;
}


</style>

