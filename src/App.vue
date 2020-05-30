<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-btn to="/">
        <v-toolbar-title>Vuetify Dashboard</v-toolbar-title>
      </v-btn>
      <v-spacer></v-spacer>
      <v-btn text rounded to="/" color="white">Home</v-btn>
        <v-btn v-for="navlink in headerNav" :key="`${navlink.label}-header-link`" text rounded :to="navlink.link"> 
          {{ navlink.label }}
        </v-btn>
    </v-app-bar>
    <v-content>
      <router-view></router-view>
    </v-content>
  <v-footer
    color="primary lighten-1"
    padless
  >
    <v-row
      justify="center"
      no-gutters
    >
    <v-btn text rounded to="/" color="white" class="my-2">Home</v-btn>
      <v-btn
        v-for="navlink in links"
        :key='`${navlink.label}-footer-link`'
        color="white"
        text
        rounded
        class="my-2"
        :to='navlink.link'
      >
        {{ navlink.label }}
      </v-btn>
      <v-col
        class="primary lighten-2 py-4 text-center white--text"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-col>
    </v-row>
  </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",
  components: {},
  data: () => ({
    links: [
      {
        label: "Login",
        link: { name: "login" },
        isHeader: true
      },
      {
        label: "Dashboard",
        link: { name: "dashboard" },
        isHeader: true
      },
      {
        label: "About Us",
        link: { name: "about-us" },
        isHeader: false
      },
      {
        label: "Team",
        link: { name: "team" },
        isHeader: false
      },
      {
        label: "Services",
        link: { name: "services" },
        isHeader: false
      },
      {
        label: "Blog",
        link: { name: "blog" },
        isHeader: false
      },
      {
        label: "Contact Us",
        link: { name: "contact-us" },
        isHeader: false
      },
      {
        label: "Register",
        link: { name: "signup" },
        isHeader: true
      }
    ]
  }),
  computed: {
    headerNav() {
      return this.links.filter(el => el.isHeader);
    }
  }
};
</script>
