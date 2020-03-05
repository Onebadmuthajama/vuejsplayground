<template>
  <v-app id="inspire">
    <v-btn
      class="ml-2 mt-2"
      x-large
      v-if="!drawer"
      @click.stop="drawer = !drawer"
      dark
      icon
      color="white"
    >
      <v-icon v-if="!drawer" dark>fa-bars</v-icon>
      <v-icon v-else dark>fa-bars</v-icon>
    </v-btn>

    <v-container>
      <v-navigation-drawer v-model="drawer" app clipped>
        <v-list dense>
          <v-list-item @click.stop="drawer = false">
            <v-list-item-action>
              <v-icon x-large>mdi-close</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>Close</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item link>
            <v-list-item-action>
              <v-icon x-large>mdi-face</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>About</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item link>
            <v-list-item-action>
              <v-icon x-large>mdi-code-tags</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>Projects</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-container>

    <v-content class="float-sm-right float-md-none">
      <v-container fluid>
        <v-row align="center" justify="center">
          <v-col class="shrink col-8">
            <v-tooltip right>
              <template v-slot:activator="{ on }">
                <v-btn
                  class="mb-2"
                  :href="source"
                  icon
                  large
                  target="_blank"
                  v-on="on"
                >
                  <v-icon large>mdi-code-tags</v-icon>
                </v-btn>
              </template>
              <span>Source</span>
            </v-tooltip>
            <v-tooltip right>
              <template v-slot:activator="{ on }">
                <v-btn
                  class="mb-2"
                  icon
                  large
                  href="https://codepen.io/johnjleider/pen/bXNzZL"
                  target="_blank"
                  v-on="on"
                >
                  <v-icon large>mdi-codepen</v-icon>
                </v-btn>
              </template>
              <span>Codepen</span>
            </v-tooltip>
            <v-expansion-panels>
              <v-expansion-panel v-for="(item, i) in languages" :key="i">
                <v-expansion-panel-header>{{ item }}</v-expansion-panel-header>
                <v-expansion-panel-content>
                  <v-expansion-panels>
                    <v-expansion-panel v-for="(item, i) in 5" :key="i">
                      <v-expansion-panel-header>Item</v-expansion-panel-header>
                      <v-expansion-panel-content>
                        Lorem ipsum dolor sit amet, consectetur adipiscing elit,
                        sed do eiusmod tempor incididunt ut labore et dolore
                        magna aliqua. Ut enim ad minim veniam, quis nostrud
                        exercitation ullamco laboris nisi ut aliquip ex ea
                        commodo consequat.
                      </v-expansion-panel-content>
                    </v-expansion-panel>
                  </v-expansion-panels>
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                  do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco
                  laboris nisi ut aliquip ex ea commodo consequat.
                </v-expansion-panel-content>
              </v-expansion-panel>
            </v-expansion-panels>
          </v-col>
        </v-row>
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; Kaden Lovell 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  props: {
    source: String
  },
  data: () => ({
    drawer: false,
    languages: ["Angular", "React", "Vue", "C#", "Java", "Python"]
  }),
  created() {
    this.$vuetify.theme.dark = true;
  }
};
</script>

<style scoped>
.sidebar {
  height: 100%; /* 100% Full-height */
  width: 0; /* 0 width - change this with JavaScript */
  position: fixed; /* Stay in place */
  z-index: 1; /* Stay on top */
  top: 0;
  left: 0;
  background-color: #111; /* Black*/
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 60px; /* Place content 60px from the top */
  transition: 0.5s; /* 0.5 second transition effect to slide in the sidebar */
}

/* The sidebar links */
.sidebar a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
  transition: 0.3s;
}

/* When you mouse over the navigation links, change their color */
.sidebar a:hover {
  color: #f1f1f1;
}

/* Position and style the close button (top right corner) */
.sidebar .closebtn {
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
  margin-left: 50px;
}

/* The button used to open the sidebar */
.openbtn {
  font-size: 20px;
  cursor: pointer;
  background-color: #111;
  color: white;
  padding: 10px 15px;
  border: none;
}

.openbtn:hover {
  background-color: #444;
}

/* Style page content - use this if you want to push the page content to the right when you open the side navigation */
#main {
  transition: margin-left 0.5s; /* If you want a transition effect */
  padding: 20px;
}

/* On smaller screens, where height is less than 450px, change the style of the sidenav (less padding and a smaller font size) */
@media screen and (max-height: 450px) {
  .sidebar {
    padding-top: 15px;
  }
  .sidebar a {
    font-size: 18px;
  }
}
</style>
