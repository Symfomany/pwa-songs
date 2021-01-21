<template>
  <div>
    <form>
      <p>Username:</p>
      <input v-model="username" />

      <p>Avatar:</p>
      <img :src="avatar" />

      <p>Ville:</p>
      <input v-model="ville" />

      <p>CP:</p>
      <input v-model="cp" @keyup="verifCP" />
      <p v-if="validCP">CP non valide</p>

      <p>Password:</p>
      <input v-model="password" />

      <p>Confirm Password:</p>
      <input
        :class="`alert ${validPass == true ? 'green' : 'red'}`"
        @keyup="verifPassword"
        v-model="repassword"
      />

      <p>Capcha:</p>
      <input v-model="capcha" />

      <button type="button"></button>
    </form>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      avatar:
        "https://www.premiere.fr/sites/default/files/styles/scale_crop_1280x720/public/2018-04/avatarbilan.jpg",
      username: "",
      ville: "",
      cp: "69003",
      password: "",
      repassword: "",
      capcha: "",
      validCP: false,
      validPass: false,
    };
  },

  watch: {},
  computed: {},
  methods: {
    verifPassword() {
      if (this.password === this.repassword) {
        this.validPass = true;
      } else {
        this.validPass = false;
      }
    },
    verifCP() {
      const reg = /^[0-9]{5}$/;

      if (reg.test(this.cp) === true) {
        this.validCP = false;
        this.avatar =
          "https://prod-ripcut-delivery.disney-plus.net/v1/variant/disney/C29D0540C44A5ADD5C5A76E861A3542AA2EE166A1182F3587C18EE0CA1202102/scale?width=1200&aspectRatio=1.78&format=jpeg";
      } else {
        this.validCP = true;
      }
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