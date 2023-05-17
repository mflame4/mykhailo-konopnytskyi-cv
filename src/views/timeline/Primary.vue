<template>
  <v-card color="grey lighten-4" light>
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Life in a Nutshell' : 'My Experiences'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline dense>
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{ transparent: item.transparent }"
            large
          >
            <template v-if="item.iconImage" v-slot:icon>
              <v-avatar>
                <img :src="publicPath(item.iconImage)" />
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex md11 sm10 xs12>
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex :md7="!!item.image" :md12="!item.image" xs12>
                        <div class="mr-1">
                          <span v-if="item.text" class="pre">{{
                            item.text
                          }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div v-else-if="item.html" v-html="item.html" />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex v-if="item.image" md5 xs12>
                        <div class="mt-2">
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem, ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="
                              item.imageHeight ? item.imageHeight : ''
                            "
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from "@/views/content/Section";
export default {
  name: "Timeline",
  components: { ContentSection },
  data: () => ({
    detailed: true,
    items: [
      {
        detailed: true,
        year: "2018",
        transparent: true,
        title: "First international robotics competitions",
        html: `
          <p>
              Team<span class="green--text accent-4">: <span class="">3 persons</span>
          </p>
          <p>
            About 20 teams participated from Moldova, Romania and Ukraine.<br/>
            The participants were engaged in the development and programming of specialized devices, including:
          <ul>
            <li>flying devices</li>
            <li>manipulators</li>
            <li>navigation systems</li>
            <li>equipment for spatial positioning</li>
          </ul>
          We managed to develop two devices based on Raspberry Pi and Arduino software modules.<br/>
            All the mechanical elements were designed independently and printed on a 3D printer, which was also made by ourselves. <br/>
              The devices can be used in a wide range of circumstances. For example, they can move small objects as well as carry out certain manipulative actions in hazardous production conditions. <br/>
          </p>
          <p><span class="light-blue--text lighten-3">That teamwork experience was extremely useful and kept improving with time.<span/></p>
        `,
        image: require("@/assets/img/timeline/earthrover.png"),
        iconImage: require("@/assets/img/timeline/robot-industrial.svg"),
      },
      {
        detailed: true,
        year: "2018-19",
        transparent: true,
        title: "Robotics and computer systems competitions",
        html: `
          <p>
            I participated and reached the top 3 in many competitions across the Ukraine and abroad.<br/>
            Most of them were about:
            <ul>
              <li>Computer networks</li>
              <li>Programming</li>
              <li>Robotics competitions</li>
              <li>Internet of thing and cyberphysics systems</li>
              </ul> 
          </p>
        `,
        image: require("@/assets/img/timeline/competitions.png"),
        imageHeight: 450,
        icon: "mdi mdi-tournament",
      },
      {
        year: "2019",
        title: "Aptis Exam",
        html: `
          <p>
              Current status: <span class="light-blue--text lighten-3">Passed for a C grade.</span>
          </p>
          <p>
            After a 2-year course at the Language Center of Chernivtsi National University, I decided to get an international certificate.<br/> 
            The exam consisted of many parts to test all abilities.<br/> <span class="light-blue--text lighten-3">It was a good experience that helped me prepare for future work and made me feel much more comfortable in stressful situations.<span/>
          </p>
        `,
        image: require("@/assets/img/timeline/aptis.png"),
        iconImage: require("@/assets/img/timeline/aptis-test.png"),
      },
      {
        year: "2020",
        title: "Got a first job! Telesuper.nl",
        html: `<p>I was excited to start working, and even better, in an international team! <br/>
        The company that I joined was from the Netherlands and was working with two big clients from the inner Dutch market. <br/></p>
        <p>My first  work assignments were to pass a decent number of courses, so while I was adapting to the company and getting more information about projects, I was successfully passing a bunch of Udemy courses, some of which were:
                    <ul>
                      <li>Vue - The Complete Guide</li>
                      <li>Learn SQL Using PostgreSQL</li>
                      <li>Git Essential Guide</li>
                      <li>Git with Bitbucket</li>
                      <li>Hibernate and JPA with Spring Boot</li>
                      </ul></p>
                      <p>Passing courses was pretty easy, and under the control of colleagues with constant code reviews, it was very efficient as well. </p>
                      <p>During the courses, I started to join all daily team Zoom calls, and thanks to those and the courses, I started to understand better how the developing ecosystems works, how workflow are built, how projects function, and how to make them consistent.</p>
                      <p>Pretty soon I started to work on one of two projects, Telesuper, which is a network of products and services for the Dutch inner market, including schools and some government organizations. I mainly worked on the ordering process and the shop frontend.</p>
                      <p>My usual tasks were: developing new features and testing them; after my pull request was approved, deployment to the test server for clients to test; if they want any changes or adjustments, redo all previous steps; and when all was approved, deployment to the staging or production server.</p>
                      <p>Maintaining projects and fixing bugs as well.
                      <p>https://www.telesuper.nl/ https://winkel.telesuper.nl/</p>
                      </p>
                      <p>We worked as a scrum team with daily meetings via Zoom, where we discussed past day progress, problems we met, if we needed help or clarification, sharing suggestions, and on what we would work on. The usual communication was via Slack.</p>
                      <p>Also, we used Jira and Confluence systems for workflow (hours log, project info, documentation, retrospectives, etc., sprints, backlogs, epics, and stories with estimations).</p>
                      <p>As for version control, we used Bitbucket, which is based on Git, and Git Flow was the usual workflow methodology.</p>`,
        image: require("@/assets/img/timeline/telesuper.png"),
        iconImage: require("@/assets/img/timeline/telesuper-icon.png"),
      },
      {
        year: "2021",
        title: "Another Project!",
        html: `<p>After the first pretty successfull year, I was invited to join a new team on another project and I started working with 2 projects at the same time.<br/></p>
                      <p>Decokay: projects about managing networks of products and decoration services, creating designs, decoration material, etc. </p>
                      <p>I also rewrote old legacy ColdFusion code to Vuejs, and after some point we started a whole new project on Vue only from scratch, I was taking part in it, developing and submitting architecture decisions. Worked most on the time on a management project that can create, change, manage, and show statistics for Decokay networks brands and items.</p>
                      <p>The workflow was the same as with the Telesuper projects.
                      <p>https://www.decokay.nl/</p>
                      </p>`,
        image: require("@/assets/img/timeline/decokay.png"),
        iconImage: require('@/assets/img/timeline/decokay-icon.png'),
      },
      {
        year: "2022-23",
        title: "Turning Point",
        html: `<p>After the Russian invasion of Ukraine, things started getting hard, and I got involved with some start-ups, so I decided to give one a shot <br/>
        </p>
        <p> The idea was to help students study the syntaxes of multiple programming languages through lessons, from the basics to the highest level. Business model was free trial and then monthly subscriptions paid through Stripe.</p>
                      <p>The front-end part was presented by a vue-keyboard that highlights and reacts at each key press, and the text field lessons data above was fetched from the back-end API. Highlighting text that was typed right, highlighting and displaying errors, and then showing general stats after the end of the session. The back-end part was filled with some basic lessons for a few languages and a connected Stripe API that would allow customers to buy subscriptions.
                      </p>
                      <p>While the project was in development, research about needed libraries and the architecture of the app was done by me, and then basic functionality with styling using Vuetify was developed. The project was not finished because all the work was suddenly stopped because the startup was cancelled.</p>
                      <p><span class="light-blue--text lighten-3">After this I decided to look for freelance jobs and improving my skills while searching!</span></p>`,
        iconImage: require("@/assets/img/timeline/Ukraine.png"),
      },
    ],
  }),
  computed: {
    orderedItems() {
      const items = [...this.items].reverse();
      if (this.detailed) return items;
      return items.filter((item) => {
        return !item.detailed;
      });
    },
  },
};
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent {
  opacity: 0.6;
}
</style>
