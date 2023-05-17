<template>
  <v-card color="grey lighten-4" light>
    <v-card-text>
      <content-section title="Who am I?">
        I enjoy working in teams and I have experience with Kanban and Scrum
        methodologies. <br />
        With 3 years of professional experience as a front-end developer and
        fundamental knowledge of the back-end. <br />
        Motivated and hardworking in my studies, I earned a master’s degree in
        computer engineering with honors as the result. <br />
      </content-section>
      <content-section v-if="prouds" title="What am I proud of?">
        <v-layout v-for="(proud, i) in prouds" :key="i">
          <v-flex md1 xs3>
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex md11 xs9>
            <p>
              <strong>{{ proud.text }}</strong
              ><br />
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section v-if="educations" title="Education">
        <v-layout v-for="(education, i) in educations" :key="i">
          <v-flex md4> {{ education.from }} - {{ education.to }} </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section v-if="skills" id="to-timeline" title="Skills">
        <template slot="actions"> </template>
        <v-layout wrap>
          <template v-for="(skill, i, j) in skills">
            <v-flex v-if="skill.divider" :key="i" md12 xs12 mb-4 />
            <v-flex v-else :key="j" md6 xs12>
              <div class="mr-2 ml-2">
                <div class="align-center">
                  <v-icon small>
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from "@/views/content/Section";
export default {
  name: "MainContent",
  components: { ContentSection },
  data: () => ({
    prouds: [
      {
        icon: "mdi mdi-code-tags",
        text: "Successfully rewrote legacy project from scratch on Vue JS",
        source: "(https://www.decokay.nl/)",
      },
      {
        icon: "mdi mdi-microsoft-teams",
        text:
          "Efficient work on 2 different projects with 2 different international teams at the same time",
        source: "(http://www.telesuper.nl/ && https://www.decokay.nl/)",
      },
      {
        icon: "mdi mdi-school",
        text: "Cerfiticated Advanced level of English language",
        source: "(https://www.britishcouncil.org/exam/aptis)",
      },
    ],
    educations: [
      {
        from: "2013",
        to: "2017",
        title: "Junior Specialist, Computer Systems and Networks",
        location: "Colleage of Chernivtsi National University",
        description: "",
      },
      {
        from: "2017",
        to: "2021",
        title: "Master degree, Internet of Things and Computer Engineering",
        location: "Chernivtsi National University",
        description: "Started working before finishing the study",
      },
    ],
    skills: [
      {
        title: "HTML",
        icon: "mdi mdi-language-html5",
        value: 95,
      },
      {
        title: "JavaScript",
        icon: "mdi-language-javascript",
        value: 80,
      },
      {
        title: "CSS",
        icon: "mdi mdi-language-css3",
        value: 90,
      },
      {
        title: "Vue.js Framework",
        icon: "mdi-vuejs",
        value: 90,
      },
      { divider: true },
      {
        title: "Amazon Web Services",
        icon: "mdi mdi-aws",
        value: 75,
      },
      {
        title: "Bitbucket",
        icon: "mdi mdi-bitbucket",
        value: 65,
      },
      {
        title: "Web Application Security",
        icon: "mdi-shield-lock",
        value: 60,
      },
      {
        title: "Unit testing",
        icon: "mdi-test-tube",
        value: 25,
      },
      {
        title: "cPanel",
        icon: "mdi mdi-server",
        value: 25,
      },
      {
        title: "Git",
        icon: "mdi-git",
        value: 70,
      },
      { divider: true },
      {
        title: "Hardware Development",
        icon: "mdi-chip",
        value: 40,
      },
      {
        title: "PostgreSQL",
        icon: "mdi mdi-database-search",
        value: 35,
      },
      { divider: true },
      {
        title: "Communication",
        icon: "mdi mdi-account-multiple",
        value: 75,
      },
      {
        title: "Ability to work in a team",
        icon: "mdi-account-group",
        value: 80,
      },
      {
        title: "Motivation",
        icon: "mdi mdi-account-alert",
        value: 98,
      },
      {
        title: "Dependability",
        icon: "mdi mdi-briefcase",
        value: 96,
      },
    ],
  }),
};
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
