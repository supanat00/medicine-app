<template>
  <v-content class="center">
    <v-card width="500" class="mx-auto mt-9">
      <v-card-title class="login-title">Login</v-card-title>
      <v-card-text>
        <v-text-field
          v-model="email"
          label="Username"
          prepend-icon="mdi-account-circle"
        />
        <v-text-field
          v-model="password"
          label="Password"
          type="password"
          prepend-icon="mdi-lock"
          :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="showPassword = !showPassword"
        />
      </v-card-text>

      <v-divider></v-divider>
      <v-card-actions>
        <v-btn color="success">Register</v-btn>
        <v-btn color="info" @click="handleLoginClicked">Login</v-btn>
      </v-card-actions>
    </v-card>
  </v-content>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    async handleLoginClicked() {
      try {
        const response = await this.$auth.loginWith('local', {
          data: { user: { email: this.email, password: this.password } },
        })
        // eslint-disable-next-line no-console
        console.log(response)
        if (response.data.success) {
          this.$router.replace({ name: 'inspire' })
        }
      } catch (err) {
        // eslint-disable-next-line no-console
        console.log(err)
      }
    },
  },
}
</script>

<script>
export default {
  layout: 'session',
}
</script>

<style lang="css" scoped>
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
.login-title {
  justify-content: center;
}
</style>
