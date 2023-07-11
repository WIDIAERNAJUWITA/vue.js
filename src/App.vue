<template>

  <v-app>

   <v-app-bar app color="primary" dark extended>

  <v-text-field
  slot="extension" 
  hide-details
  append-icon="mdi-microphone"
  flat
  label="Search"
  prepend-inner-icon="mdi-magnify"
  solo-inverted
></v-text-field>
  <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

  <v-toolbar-title>Vueshop</v-toolbar-title>

  <!-- pemisah konten -->
  <v-spacer></v-spacer>

 <v-btn icon to="/about">
    <v-badge color="orange" overlap>
      <template v-slot:badge>
        <span>3</span>
      </template>
      <v-icon>mdi-cart</v-icon>
    </v-badge>
  </v-btn>
</v-app-bar>

    <v-card>
  <v-navigation-drawer app  v-model="drawer">

    <div class="pa-2" v-if="guest">
  <v-btn block color="primary" class="mb-1">
    <v-icon left>mdi-lock</v-icon>
      Login
  </v-btn>
  <v-btn block color="success">
    <v-icon left>mdi-account</v-icon>
      Register
  </v-btn>
</div>
  
   <v-list>

  <v-list-item v-if="!guest">
  <v-list-item-avatar>
    <v-img src="data:image/jpeg;base64,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"></v-img>
  </v-list-item-avatar>
  <v-list-item-content>
    <v-list-item-title>Widia Erna Juwita</v-list-item-title>
  </v-list-item-content>
</v-list-item>
<v-divider></v-divider>

   
  <v-list-item
    v-for="(item, index) in menus"
    :key="`menu-`+index"
    :to="item.route"
    
  >
  
    <v-list-item-icon>
      <v-icon left>{{ item.icon }}</v-icon>
    </v-list-item-icon>

    <v-list-item-content>
      <v-list-item-title>{{ item.title }}</v-list-item-title>
    </v-list-item-content>
  </v-list-item>
</v-list>

<template v-slot:append v-if="!guest">
        <div class="pa-2">
          <v-btn block color="red" dark @click="logout">
            <v-icon left>mdi-lock</v-icon>
              Logout
          </v-btn>
        </div>
      </template>

  </v-navigation-drawer>
</v-card>

    <v-content>
      <v-container fluid>
        <!-- jika menggunakan vue-router -->
        <router-view></router-view>
      </v-container>
    </v-content>

    <v-card>
  <v-footer absolute app>
    <v-card-text class="text-center">
      &copy; {{ new Date().getFullYear() }} — <strong>Vueshop</strong>
    </v-card-text>
  </v-footer>
</v-card>

  </v-app>
</template>
...
<script>
export default {
  name: 'App',
  data: () => ({
  drawer: false,
  menus: [
    { title: 'Home', icon: 'mdi-home', route: '/' },
    { title: 'About', icon: 'mdi-account', route: '/about' },
  ],
  guest: false, // <= tambahkan ini
})
};

</script>