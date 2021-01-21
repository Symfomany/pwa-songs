<template>
  <div>
    <form>
      <p>Nom:</p>
      <v-text-field
        v-model="nom"
        @keyup="verifNom"
        :rules="nameRules"
        :counter="10"
        label="First name"
        required
      ></v-text-field>
      <p :class="classNom" v-if="validNom == false">{{ messageErreur }}</p>
      <p>Sujet</p>
      <input @keyup="verifSujet" v-model="sujet" />
      <p v-if="sujet.length > 0" :class="classSujet">
        {{ messageErreurSujet }}
      </p>

      <p>Email</p>
      <input @keyup="verif" v-model="email" />
      <p class="red" v-if="validEmail == false">Votre email est invalide</p>
      <p>Contenu</p>
      <textarea v-model="contenu"></textarea>
      <p>Nb de mots: {{ nbMots }} mots</p>
      <br />
      <button :disabled="!verifAll" type="button" @click="send">
        Envoyer cet email
      </button>
    </form>

    <div v-if="valid === true">
      <p>Nom: {{ nom }}</p>
      <p>Sujet: {{ sujet }}</p>
      <p>Email: {{ email }}</p>
      <p>Contenu: {{ contenu }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      nom: "",
      sujet: "",
      email: "",
      contenu: "",
      validEmail: true,
      validNom: true,
      validSujet: true,
      nbMots: 0,
      valid: false,
      classNom: "red",
      classSujet: "red",
      messageErreur: "Votre nom est trop court",
      messageErreurSujet: "Votre sujet est pas valide !",
    };
  },

  watch: {
    contenu(val) {
      this.nbMots = val.split(" ").length;
    },
  },

  computed: {
    verifAll() {
      return this.validSujet && this.validNom && this.validEmail;
    },
  },
  methods: {
    verifSujet() {
      if (this.sujet.length < 5 || this.sujet.length > 30) {
        this.validSujet = false;
        this.messageErreurSujet = "Votre sujet est pas valide !";
        this.classSujet = "red";
      } else {
        this.validSujet = true;
        this.messageErreurSujet = "Sujet OK!";
        this.classSujet = "green";
      }
    },
    verif() {
      const regex = /\S+@\S+\.\S+/;
      if (regex.test(this.email) == false) {
        this.validEmail = false;
      } else {
        this.validEmail = true;
      }
    },
    verifNom() {
      if (this.nom.length < 3) {
        this.validNom = false;
        this.classNom = "red";
        this.messageErreur = "Votre nom est trop court!";
      } else {
        this.classNom = "green";
        this.validNom = true;
        this.messageErreur = "Votre nom est OK !";
      }
    },
    send() {
      console.log(this.nom, this.sujet, this.email, this.contenu);
      this.valid = true;
    },
  },
};
</script>

<style>
.red {
  color: red;
}
.green {
  color: green;
}
</style>