<template>
  <v-container>
    <contact></contact>

    <v-row class="text-center">
      <v-col cols="12">
        <v-alert type="success">Votre nom est OK!</v-alert>
        <prenom :nom="nom"></prenom>

        <v-btn elevation="2" color="pink  lighten-4">My Button</v-btn>
        <v-btn color="indigo darken-4 white--text">My Button 2</v-btn>

        <v-card class="mx-auto" max-width="400" tile>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Single-line item</v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-item two-line>
            <v-list-item-content>
              <v-list-item-title>Two-line item</v-list-item-title>
              <v-list-item-subtitle>Secondary text</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <v-list-item three-line>
            <v-list-item-content>
              <v-list-item-title>Three-line item</v-list-item-title>
              <v-list-item-subtitle>
                Secondary line text Lorem ipsum dolor sit amet,
              </v-list-item-subtitle>
              <v-list-item-subtitle>
                consectetur adipiscing elit.
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Prenom from "./Prenom.vue";
import Contact from "./Contact.vue";

export default {
  name: "HelloWorld",

  components: {
    prenom: Prenom,
    contact: Contact,
  },
  data: () => ({
    nom: "Boyer",
  }),
};
</script>
