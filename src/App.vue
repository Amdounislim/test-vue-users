<template>
  <v-app>
    <Header v-on:add-user="addUser" />
    <!-- <AddUser v-on:add-user="addUser" /> -->
    <UserList v-on:delete-user="deleteUser" v-bind:users="users" />
  </v-app>
</template>

<script>
// import AddUser from './components/AddUser.vue';
import Header from "./components/Header.vue";
import UserList from "./components/UserList.vue";

export default {
  name: "App",
  components: {
    Header,
    UserList,
    // AddUser,
  },
  data() {
    return {
      users: [
        {
          id: Math.random(),
          firstName: "Jason",
          lastName: "Momoa",
          email: "json@gmail.com",
        },
        {
          id: Math.random(),
          firstName: "Johnny",
          lastName: "Depp",
          email: "jhonny@gmail.com",
        },
        {
          id: Math.random(),
          firstName: "Steve",
          lastName: "Harvey",
          email: "steve@gmail.com",
        },
        {
          id: Math.random(),
          firstName: "Taylor",
          lastName: "Swift",
          email: "taylor@gmail.com",
        },
      ],
    };
  },

  methods: {
    addUser(newUser) {
      this.users = [...this.users, newUser];
    },
    deleteUser(id) {
      this.users = this.users.filter((user) => user.id !== id);
    },
  },
};
</script>
