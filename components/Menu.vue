<template>
  <v-navigation-drawer v-model="drawer" fixed left class="d-block">
    <v-container fluid class="jello-topbar">
      <v-row no-gutters align="center" justify="space-between">
        <v-icon @click="drawer = false">mdi-close</v-icon>

        <v-row no-gutters align="center" justify="end" class="pl-12">
          <v-list-item>
            <v-list-item-avatar>
              <v-img src="https://avatars.mds.yandex.net/i?id=cc81e36dc1a3641e296d6912d35e5cb3-5558053-images-thumbs&n=13"></v-img>
            </v-list-item-avatar>
          </v-list-item>
        </v-row>
      </v-row>
      <v-list>
        <v-list-item link>
          <v-list-item-content>
            <v-list-item-title class="text-h6">
              Vladimir Guziuk
            </v-list-item-title>
            <v-list-item-subtitle>{{ $nuxt.$fire.auth.currentUser.email }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-container>
    <v-container class="d-block menu-items">
      <div class="d-flex flex-column">
        <div class="d-flex">
          <br />

        </div>
        <div class="d-flex">
          <nuxt-link to="/">
            <v-icon>mdi-view-dashboard-variant-outline</v-icon>&nbsp;&nbsp;<b>My Boards</b>
          </nuxt-link>
        </div>
        <div class="d-flex">
          <nuxt-link to="/supply">
            <v-icon>mdi-exit-to-app</v-icon>&nbsp;&nbsp;<b>Supply</b>
          </nuxt-link>
        </div>
        <div class="d-flex">
          <nuxt-link to="/auth/signout">
            <v-icon>mdi-exit-to-app</v-icon>&nbsp;&nbsp;<b>Sign out</b>
          </nuxt-link>
        </div>
      </div>
    </v-container>
  </v-navigation-drawer>
</template>

<script>
export default {
  name: "Menu",
  props: {
    drawer: {
      default: false,
    },
  },

}
</script>

<style scoped>

</style>
