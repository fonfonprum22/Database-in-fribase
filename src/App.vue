<template>
  <v-app>
    <v-app-bar
      app
      color="teal lighten-3"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://scontent.fbkk2-3.fna.fbcdn.net/v/t1.15752-9/121490399_395691291431137_6114714965204409378_n.png?_nc_cat=111&_nc_sid=ae9488&_nc_eui2=AeGhM0S9ibweKaIfXuZApRDS1vAJcr7we4_W8AlyvvB7j2F2LMEy_4NlEu1LqIxWMnceDzJVT-C3BMEkl55Lmx-I&_nc_ohc=TZHDL4zELgEAX-pWztk&_nc_ht=scontent.fbkk2-3.fna&oh=a230b344a3f9b4237c3009c5a76b7128&oe=5FAACD87"
          transition="scale-transition"
          width="40"
        />
        <b>
          <h3>MyStore</h3>
        </b>
      </div>

      <v-spacer></v-spacer>

      <v-btn 
      to="/"
      >
        firebase
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

