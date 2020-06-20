<template>
  <v-app>
    <v-navigation-drawer
            v-model="drawer"
            :mini-variant.sync="mini"
            absolute
            permanent
    >
      <v-list-item class="px-2">
        <v-list-item-avatar>
          <v-img src="./assets/logo-60x60.png"></v-img>
        </v-list-item-avatar>

        <v-list-item-title>Creative Coiffeur</v-list-item-title>

        <v-btn
                icon
                @click.stop="mini = !mini"
        >
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-item
                v-for="item in items"
                :key="item.title"
                :to="item.link"
                link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
    drawer: true,
    items: [
      { title: 'Home', icon: 'mdi-home-city', link: '/' },
      { title: 'Neuer Termin', icon: 'mdi-calendar-clock', link: '/new-event' },
      { title: 'Terminübersicht', icon: 'mdi-calendar-multiple', link: '/events-list' },
      { title: 'Neuer Kunde', icon: 'mdi-account-plus', link: '/new-user' },
      { title: 'Kundenstamm', icon: 'mdi-account-group-outline', link: '/user-list' },
    ],
    mini: true
  }),
};
</script>
