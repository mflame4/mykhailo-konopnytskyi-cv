<template>
  <v-app>
    <v-content>
      <template-container />
    </v-content>
  </v-app>
</template>

<script>
import TemplateContainer from "@/views/Container";

export default {
  name: "App",
  components: { TemplateContainer },
  data() {
    return {};
  },
};
</script>
