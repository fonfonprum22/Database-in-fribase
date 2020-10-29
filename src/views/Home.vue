<template>
  <div class="form">
    <v-form ref="form" v-model="valid" lazy-validation id="form">
      <v-card class="mx-auto" max-width="5000" outlined id="card">
        <v-card-title> Form </v-card-title>
        <v-card-subtitle> Input Data Information </v-card-subtitle>
        <v-col>
          <v-text-field
            v-model="user.name"
            :rules="[(v) => !!v || 'Name is required']"
            required
            label="Name"
          />
          <v-text-field
            v-model="user.lastName"
            :rules="[(v) => !!v || 'lastName is required']"
            required
            label="LastName"
          />
          <v-text-field
            type="number"
            v-model="user.Phone"
            :rules="[(v) => !!v || 'Phone is required']"
            required
            label="Phone"
          />
          <v-text-field
            v-model="user.email"
            :rules="[(v) => !!v || 'email is required']"
            required
            label="Email"
          />
          <v-btn
            outlined
            rounded
            text
            :disabled="!valid"
            color="success"
            class="mr-4"
            @click="add_user()"
            >submit
          </v-btn>
        </v-col>
      </v-card>
    </v-form>
    <v-alert v-if="adduser" outlined text type="success"
      >add user success!!</v-alert
    >
  </div>
</template>

<script>
import firebase from "firebase";
export default {
  data: () => ({
    valid: true,
    adduser: false,
    user: {
      name: "",
      lastName: "",
      Phone: "",
      email: "",
    },
  }),
  methods: {
    add_user() {
      firebase
        .firestore()
        .collection("user")
        .add(this.user)
        .then((res) => {
          this.adduser = true;
          console.log(res + "add user");
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },

  created() {
    const config = {
      apiKey: "AIzaSyD_rFT5D-ggnuniKLr7LKYciOXHd04kVUM",
      authDomain: "databasemystore.firebaseapp.com",
      databaseURL: "https://databasemystore.firebaseio.com",
      projectId: "databasemystore",
      storageBucket: "databasemystore.appspot.com",
      messagingSenderId: "449171447043",
      appId: "1:449171447043:web:e9112ff586a205f6ea1d36",
      measurementId: "G-WV6PQNKY6F",
    };
    firebase.initializeApp(config);
    firebase.analytics();
  },
};
</script>

<style>
#form {
  background-color: #fded57;
  padding: 60px;
}
#card {
  width: 100%;
  background-color: white;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.5), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
</style>