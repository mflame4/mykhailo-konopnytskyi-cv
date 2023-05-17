<template>
  <div class="text-md-center">
    <v-avatar color="grey lighten-4" size="120">
      <img
        id="avatar"
        src="@/assets/img/avatar.jpg"
        alt="Mykhailo Konopnytskyi"
      />
    </v-avatar>
  </div>
</template>

<script>
export default { name: "Avatar" };
</script>

<style scoped>
#avatar {
  object-fit: cover;
}
</style>
