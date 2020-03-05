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
