<template>
  <div>
    <v-system-bar color="deep-purple darken-3"></v-system-bar>

    <v-app-bar
        color="deep-purple accent-4"
        dark
        prominent
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>SISTEMA DE VENTA DE PRODUCTOS ELECTRÓNICOS</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-filter</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer
        v-model="drawer"
        absolute
        bottom
        temporary
    >
      <v-list
          nav
          dense
      >
        <v-list-item-group
            v-model="group"
            active-class="deep-purple--text text--accent-4"
        >
          <v-list-item v-for="route in routes"
                       :key="route.name"
                       @click="redirectTo(route.name)"
                       :disabled="currentRoute === route.name">
            <v-list-item-icon>
              <v-icon>{{ route.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-title>{{ route.title }}</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-card-text>

    </v-card-text>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  data() {
    return {
      drawer: false,
      group: null,
      routes: [
        {
          icon: 'mdi-home',
          title: 'Inicio',
          name: 'Home'
        },
        {
          icon: 'mdi-border-all',
          title: 'Productos',
          name: 'Product'
        },
        {
          icon: 'mdi-account',
          title: 'Acerca',
          name: 'About'
        }
      ]
    }
  },
  watch: {
    group() {
      this.drawer = false
    },
  },
  computed: {
    currentRoute() {
      return this.$route.name
    }
  },
  methods: {
    redirectTo(nameRoute) {
      this.$router.push({name: nameRoute})
    }
  },
}
</script>

<style scoped>

</style>