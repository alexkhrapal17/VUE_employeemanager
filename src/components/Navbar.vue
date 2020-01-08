<template>
  <nav>
    <div class="nav-wrapper light-blue accent-4">
      <div class="container">
        <router-link to="/" class="logo">EM</router-link>
        <ul class="nav-list right">
          <li v-if="isLoggedIn">
              <span class="email white-text">{{ currentUser }}</span>
          </li>
          <li v-if="isLoggedIn" class="hide-on-small-only">
            <router-link to="/">Dashboard</router-link>
          </li>
          <li v-if="!isLoggedIn">
            <router-link to="/login">Login</router-link>
          </li>
          <li v-if="!isLoggedIn">
            <router-link to="/register">Register</router-link>
          </li>
          <li v-if="isLoggedIn">
            <button @click="logout" class="btn black show-on-large hide-on-small-only">Logout</button>
            <button @click="logout" class="btn black show-on-small hide-on-large-only"><i class="fa fa-sign-out"></i></button>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import firebase from "firebase";

export default {
  name: "Navbar",
  data() {
    return {
      isLoggedIn: false,
      currentUser: false
    };
  },
  created() {
    if (firebase.auth().currentUser) {
      this.isLoggedIn = true;
      this.currentUser = firebase.auth().currentUser.email;
    }
  },
  methods: {
    logout() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.go({ path: this.$router.path });
        });
    }
  }
};
</script>

<style scoped>
.nav-list {
  display: flex;
  align-items: center;
}

.email {
    padding-right: 10px;
}

.logo {
  font-size: 30px;
  line-height: 66px;
  cursor: pointer;
  font-weight: 700;
  transition: all .3s ease-in-out;
}

.logo:hover {
  color: #eee;
}

@media (max-width: 650px) {
    .logo {
      line-height: 56px;
    }
}
</style>