<template>
  <div class="my-app">
    <h1>Witaj w systemie do zapisów na zajecia</h1>

    <div v-if="loggedIn">
    Witamy!
    <div>
      <button @click="backToMainPage()">Wyloguj</button>
    </div>
  </div>
    <div v-else>

    <input type="email" v-model="email">
    <button @click="checkIfProperAddress()">Wchodzę</button>
  </div>

    <p>Twój e-mail to {{ email }}</p>
    <div v-if="!email.includes('@')"> Twoj adres email nie zawiera @</div>
    <div v-if="email.length"> Twoj adres email ma ({{ email.length }}) znaki</div>
    <div v-if="email.length < 10"> Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15"> (Twój adres e-mail jest w sam raz.</div>
    <div v-else> Twój adres e-mail jest stanowczo za długi.</div>
  </div>
</template>

<script>
export default {

  data() {
    return {
      email: 'MWO',
      password: '',
      loggedIn: false
    };
  },
  methods: {
    logMeIn() {
      this.loggedIn = true;
    },

    checkIfProperAddress() {
      if (this.email.includes('@')) {
        this.loggedIn = true;
      }
    },

    backToMainPage() {
      this.loggedIn = false;
      this.email = '';
    }
  }
}
</script>

<style>
.my-app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
