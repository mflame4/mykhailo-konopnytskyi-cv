<template>
  <v-app id="TemplateContainer">
    <v-fade-transition mode="out-in" type="animation">
      <v-content>
        <v-container fluid fill-height>
          <github-ribbon />
          <v-layout align-center justify-center>
            <v-flex md10 sm12>
              <v-layout wrap>
                <v-flex md4>
                  <sidebar-container class="fill-height" />
                </v-flex>
                <v-flex md8>
                  <content-container class="fill-height" />
                </v-flex>
              </v-layout>
              <v-layout>
                <v-flex md12>
                  <timeline-primary />
                  <ending />
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </v-container>
      </v-content>
    </v-fade-transition>
  </v-app>
</template>

<script>
import SidebarContainer from "@/views/sidebar/Container";
import ContentContainer from "@/views/content/Container";
import TimelinePrimary from "@/views/timeline/Primary";
import Ending from "@/views/timeline/Ending";
import LeaderLine from "leader-line";
import GithubRibbon from "@/views/GithubRibbon";

export default {
  name: "TemplateContainer",
  components: {
    GithubRibbon,
    Ending,
    TimelinePrimary,
    ContentContainer,
    SidebarContainer,
  },
  mounted() {
    // eslint-disable-next-line no-unused-vars
    const line = new LeaderLine(
      document.getElementById("to-timeline"),
      document.getElementById("timeline"),
      {
        size: 2,
        color: this.$vuetify.theme.primary,
        startLabel: LeaderLine.captionLabel("To the Journey ..."),
      }
    );
  },
};
</script>

<style scoped>
#TemplateContainer{
  height: 100%;
  background: #4c4c91;
  background-image: url("../background.png") !important;
  background-size: cover;
}
</style>
