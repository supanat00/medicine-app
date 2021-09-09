<template>
  <v-app>
    <!-- app-bar -->

    <v-app-bar app dense color="warning">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>HITRIX</v-toolbar-title>

      <v-spacer></v-spacer>
    </v-app-bar>

    <!-- content  -->
    <Nuxt />
    <!-- logout-card  -->
    <v-dialog v-model="dialog" width="500">
      <v-card>
        <v-card-title> Failed to logout </v-card-title>

        <v-card-text> database is not connected. </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="dialog = false"> I accept </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <!-- drawer -->
    <v-navigation-drawer v-model="drawer" absolute temporary>
      <v-list-item>
        <v-list-item-avatar>
          <v-img src="https://randomuser.me/api/portraits/men/78.jpg"></v-img>
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title class="profile-fullname"
            >John Leider</v-list-item-title
          >
          <v-list-item-subtitle class="profile-email"
            >sandra_a88@gmail.com</v-list-item-subtitle
          >
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-item v-for="item in items" :key="item.title" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <div class="btn-logout" align="center" v-bind="attrs" v-on="on">
        <v-btn
          class="btn-red"
          outlined
          color="red"
          elevation="4"
          small
          @click="dialog = !dialog"
          >Logout</v-btn
        >
      </div>
    </v-navigation-drawer>

    <!-- Footer -->
    <v-footer app>
      <Footer />
    </v-footer>
  </v-app>
</template>
<script>
export default {
  data() {
    return {
      drawer: null,
      items: [
        { title: 'Home', icon: 'mdi-home-city' },
        { title: 'Chanels', icon: '' },
        { title: 'About', icon: '' },
      ],
      dialog: null,
    }
  },
}
</script>
<style lang="scss">
@import '~vuetify/src/components/VStepper/_variables.scss';

.btn-logout {
  padding: $stepper-step-padding;
}
</style>
