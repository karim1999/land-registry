<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item link to="/">
          <v-list-item-action>
            <v-icon>mdi-account</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Owners</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link to="/lands">
          <v-list-item-action>
            <v-icon>mdi-island</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Lands</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="indigo" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Land Registry</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer color="indigo" app>
      <span class="white--text">&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>
<script>
export default {
  props: {},
  data: () => ({
    drawer: null,
  }),
}
</script>
<style></style>
