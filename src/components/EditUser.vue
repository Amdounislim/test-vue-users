<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" persistent max-width="600px">
      <template v-slot:activator="{ on, attrs }">
        <v-btn outlined rounded text color="primary" v-bind="attrs" v-on="on">
          Edit
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5">Edit User</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="6">
                <v-text-field
                  label="first name*"
                  v-model="firstName"
                  required
                ></v-text-field>
              </v-col>

              <v-col cols="12" sm="6" md="6">
                <v-text-field
                  label="last name*"
                  v-model="lastName"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Email*"
                  v-model="email"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="dialog = false">
            Close
          </v-btn>
          <v-btn color="blue darken-1" text @click="editUser"> Save </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
export default {
  name: "EditUser",
  props: ["user"],
  data() {
    return {
      dialog: false,
      firstName: this.user.firstName,
      lastName: this.user.lastName,
      email: this.user.email,
    };
  },

   methods: {
    editUser() {
      const setUser = {
        id: this.user.id,
        firstName: this.firstName,
        lastName: this.lastName,
        email: this.email,
      };
      // Send up to parent
      this.$emit("edit-user", setUser);

      this.firstName = "";
      this.lastName = "";
      this.email = "";
      this.dialog = false
    },
  },
};
</script>