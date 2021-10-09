<template>
  <v-app-bar app color="primary" dark class="mb-2">
    <div class="d-flex align-center">
      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2"
        contain
        src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
        transition="scale-transition"
        width="40"
      />

      <v-img
        alt="Vuetify Name"
        class="shrink mt-1 hidden-sm-and-down"
        contain
        min-width="100"
        src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
        width="100"
      />
    </div>

    <v-spacer></v-spacer>
    <AddUser v-on:add-user="$emit('add-user', newUser)" />
  </v-app-bar>
</template>

<script>
import AddUser from "./AddUser.vue";
export default {
  components: { AddUser },
  name: "Header",
};
</script>
