<template>
  <v-card color="grey darken-3" dark>
    <v-card-text>
      <div class="text-sm-center mb-4 mt-3">
        <avatar />
        <h1>
          Mykhailo
          <span class="light-blue--text text--lighten-3">Konopnytskyi</span>
        </h1>
        <h2>
          Frontend Developer
        </h2>
      </div>
      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{ items }">
          <v-container pa-0>
            <v-layout wrap class="text-xs-center">
              <template v-for="(item, i) in items">
                <v-flex :key="i" md3 sm4 xs6>
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{ item }">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from "@/views/sidebar/Avatar";
import SidebarSection from "@/views/sidebar/Section";
export default {
  name: "Sidebar",
  components: { SidebarSection, Avatar },
  data() {
    return {
      sections: {
        info: {
          title: "INFO",
          items: [
            {
              name: "Email",
              icon: "mdi mdi-email-alert",
              text: "mikhail.konopnytskyi@gmail.com",
            },
            {
              name: "Developing myself and Deploying code",
              icon: "mdi-map-marker",
              text: "Ukraine, Chernivtsi",
            },
            {
              name: "BirthDay",
              icon: "mdi mdi-cake-layered",
              text: "Nov 21, 1997",
            },
          ],
        },
        socials: {
          title: "SOCIALS",
          items: [
            {
              icon: "mdi mdi-github",
              text: "GitHub",
              link: "https://github.com/mflame4",
            },
            {
              icon: "mdi mdi-linkedin",
              text: "LinkedIn",
              link: "https://www.linkedin.com/in/mykhailo-konopnytskyi/",
            },
          ],
        },
        hobbies: {
          title: "HOBBIES",
          items: [
            {
              icon: "mdi mdi-robot-happy",
              text: "Robotics",
            },
            {
              icon: "mdi-image-filter-hdr",
              text: "Camping",
            },
            {
              icon: "mdi mdi-shoe-sneaker",
              text: "Exercising",
            },
            {
              icon: "mdi-music",
              text: "Music",
            },
            {
              icon: "mdi mdi-android",
              text: "Killing Bugs",
            },
          ],
        },
        languages: {
          title: "LANGUAGES",
          items: [
            {
              text: "English",
              value: 90,
            },
            {
              text: "Ukrainian",
              value: 100,
            },
            {
              text: "Russian ",
              value: 80,
            },
          ],
        },
      },
    };
  },
};
</script>

<style scoped>
#sidebar {
  background: #2e2e2e;
}
</style>
