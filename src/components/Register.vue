<template>
  <div class="wrapper page">
    <div class="auth-form register card-panel black-text center">
      <h3>Register</h3>
      <form action="index.html">
        <div class="input-field">
          <i class="material-icons prefix">email</i>
          <input type="email" id="email" v-model="email" autocomplete="off" />
          <label for="email">Email Address</label>
        </div>
        <div class="input-field">
          <i class="material-icons prefix">lock</i>
          <input type="password" id="password" v-model="password" autocomplete="off" />
          <label for="password">Password</label>
        </div>
        <button
          @click="register"
          class="btn btn-large btn-extended grey lighten-4 black-text"
        >Register</button>
      </form>
    </div>
  </div>
</template>

<script>
import firebase from "firebase";

export default {
  name: 'Register',
  data: function() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    register: function(e) {
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.email, this.password)
        .then(
          user => {
            this.$router.go({path: this.$router.path});
          },
          err => {
            alert(err.message);
          }
        );
      e.preventDefault();
    }
  }
};
</script>