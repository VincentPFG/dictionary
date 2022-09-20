<template>
  <v-app dark>
    <v-app-bar
      app
      dense
    >
      <v-spacer />
      <v-form>
        <v-text-field
          dense
          name="word"
          outlined
          autofocus
          hide-details
          autocapitalize="none"
        />
      </v-form>
      <v-spacer />
      <v-btn-toggle multiple>
        <v-btn to="en">
          EN
        </v-btn>
        <v-btn to="es">
          ES
        </v-btn>
      </v-btn-toggle>
    </v-app-bar>
    <v-main>
      <!-- <v-container> -->
      <Nuxt />
      <!-- </v-container> -->
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
