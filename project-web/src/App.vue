<template>
  <v-app id="inspire">
    <v-system-bar color="primary" dark>
      <v-spacer></v-spacer>
      <v-icon>mdi-wifi-strength-4</v-icon>
      <v-icon>mdi-signal-cellular-outline</v-icon>
      <v-icon>mdi-battery</v-icon>
      <span>18:30</span>
    </v-system-bar>

    <v-app-bar app     
      color="blue accent-6"
      height="57"
      dense
      dark
      flat
      >
      
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>PLAYER'S PROFILE - SOCCER </v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" class = "blue accent-8" app>
      <v-list v-model="user">
        <v-list-item class="px-15">
          <v-list-item-avatar size="150">
            <v-img :src="user.picture"></v-img>
          </v-list-item-avatar>
        </v-list-item>

        <v-list-item link>
          <v-list-item-content>
            <v-list-item-title class="text-h6">
              {{ user.name }}
            </v-list-item-title>
            <v-list-item-subtitle>{{ user.email }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-divider></v-divider>

      <v-list nav dense>
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.path"
          link
        >
          <v-list-item-icon>
            <v-icon>mdi-{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <router-view></router-view>
    </v-main>

    <v-footer padless class = "blue accent-15" >
      <v-col class="text-center" cols="200">
        {{ new Date().getFullYear() }} — <strong>Otavio Cordeiro</strong>
      </v-col>
    </v-footer>

    <v-bottom-navigation v-model="value" :input-value="active" color="green">
      <v-btn>
        <span>Top Scorers</span>
        <v-icon>mdi-soccer</v-icon>
      </v-btn>

      <v-btn>
        <span>Your Data</span>
        <v-icon>mdi-account</v-icon>
      </v-btn>

      <v-btn>
        <span>Table</span>
        <v-icon>mdi-table</v-icon>
      </v-btn>
    </v-bottom-navigation>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    user: {
      name: "Mário Sérgio(Marinho)",
      email: "marinho@santosfc.com",
      picture: "marinho2.jpg",
    },
    items: [
      {
        title: "Home",
        icon: "home",
        path: "/",
      },
      {
        title: "Your titles",
        icon: "trophy",
        path: "/titles",
      },
            {
        title: "Calendar",
        icon: "calendar",
        path: "/calendar",
      },
    ],
  }),
};
</script>