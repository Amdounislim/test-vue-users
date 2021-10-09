<template>
  <v-app>
    <v-app-bar app color="primary" dark class="mb-2">
      <div class="d-flex align-center">
        <h1>User List</h1>
      </div>

      <v-spacer></v-spacer>
      <AddUser v-on:add-user="addUser" v-on:edit-user="editUser" />
    </v-app-bar>
    <UserList
      v-on:delete-user="deleteUser"
      v-on:edit-user="editUser"
      v-bind:users="users"
    />
  </v-app>
</template>

<script>
import AddUser from './components/AddUser.vue';
import UserList from "./components/UserList.vue";

export default {
  name: "App",
  components: {
    UserList,
    AddUser,
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
    addUser(user) {
      this.users = [...this.users, user];
    },
    deleteUser(id) {
      this.users = this.users.filter((user) => user.id !== id);
    },

    editUser(id, userToEdit) {
      console.log(id)
      console.log(userToEdit)
      this.users = this.users.map(user => user.id === id ? userToEdit  : user)
    },
  },
};
</script>
