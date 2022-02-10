<template>
  <v-app>
    <v-sheet color="#689CD2" height="100%">
      <v-content >
        <div class="d-block">
          <v-container fluid class="jello-topbar">
            <v-row no-gutters align="center" justify="start">
              <v-col cols="1" class="flex-grow-0 flex-shrink-0">
                <v-icon @click="drawer = true">mdi-menu</v-icon>
              </v-col>
              <v-col
                cols="1"
                style="min-width: 100px; max-width:100%;"
                class="flex-grow-1 flex-shrink-0"
              >
                <v-row no-gutters class="mb-4 pl-10 pr-8 d-flex justify-space-between align-center">
                  <nuxt-link to="/mainPage">
                    <v-row no-gutters align="center" justify="center">
                      <v-img class="image2" src="http://cdn.onlinewebfonts.com/svg/img_233159.png"></v-img>

                    </v-row>
                  </nuxt-link>
                    <nuxt-link to="/">
                      <v-row no-gutters align="center" justify="center">
                        <v-img class="image" src="https://library.kissclipart.com/20180925/ucq/kissclipart-project-management-clipart-project-management-prog-ff9c89e600ea08e4.png"></v-img>

                      </v-row>
                    </nuxt-link>
                    <nuxt-link to="/calendar">
                      <v-row no-gutters align="center" justify="center">
                        <v-img class="image" src="http://cdn.onlinewebfonts.com/svg/img_509380.png"></v-img>

                      </v-row>
                    </nuxt-link>
                    <nuxt-link to="/people">
                      <v-row no-gutters align="center" justify="center">
                        <v-img class="image" src="http://cdn.onlinewebfonts.com/svg/img_542889.png"></v-img>
                      </v-row>
                    </nuxt-link>
                  <nuxt-link to="/">
                    <v-row no-gutters align="center" justify="center">
                      <v-img class="image" src="http://cdn.onlinewebfonts.com/svg/img_461123.png"></v-img>
                    </v-row>
                  </nuxt-link>
                  <nuxt-link to="/">
                    <v-row no-gutters align="center" justify="center">
                      <v-img class="image" src="http://cdn.onlinewebfonts.com/svg/img_573293.png"></v-img>
                    </v-row>
                  </nuxt-link>
                  <nuxt-link to="/">
                    <v-row no-gutters align="center" justify="center">
                      <v-img class="image" src="http://cdn.onlinewebfonts.com/svg/img_53162.png"></v-img>
                    </v-row>
                  </nuxt-link>
                  <nuxt-link to="/">
                    <v-row no-gutters align="center" justify="center">
                      <v-img class="image" src="http://cdn.onlinewebfonts.com/svg/img_451931.png"></v-img>
                    </v-row>
                  </nuxt-link>
                  <nuxt-link to="/message_board">
                    <v-row no-gutters align="center" justify="center">
                      <v-img class="image" src="http://cdn.onlinewebfonts.com/svg/img_65825.png"></v-img>
                    </v-row>
                  </nuxt-link>
                </v-row>
              </v-col>
            </v-row>
          </v-container>
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
        </div>
        <!-- content -->
        <nuxt />
      </v-content>
    </v-sheet>

  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false
    }
  },
}
</script>

<style lang="scss" scoped>
.image{
  height: 50px;
  width: 50px;

}
.image2{
  height: 50px;
  width: 65px;

}
a {
  text-decoration: none;
}
.menu-items a {
  color: $text-color;
  padding: 10px 0px 10px 3px;
  font-size: 24px;
}
</style>
