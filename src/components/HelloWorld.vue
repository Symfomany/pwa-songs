<template>
  <div class="hello">
    <h1>Bonjour Ynov Promotion!</h1>
    <h3>Bienvenue sur le cours de la PWA</h3>
    <prenom></prenom>
    <contact></contact>

    <p>Votre age est : {{ age }} ans</p>
    <p>Votre ville est : {{ ville }}</p>
  </div>
</template>

<script>
import "./style.css";
import Prenom from "./Prenom";
import Contact from "./Contact";

export default {
  name: "HelloWorld",
  data: () => {
    return {
      age: 32,
      ville: "Lyon",
    };
  },
  props: {
    msg: String,
  },
  components: {
    prenom: Prenom,
    contact: Contact,
  },
};
</script>
