<template>
  <div id="app">
    <Navbar/>
    <div class="container">
      <div class="main-wrap">
        <router-view/>
      </div>
    </div>
    <span class="alex-khrapal">Alexander Khrapal</span>
  </div>
</template>

<script>
import Navbar from './components/Navbar';

export default {
  name: 'App',
  components: {
    Navbar
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Oswald:300,400,600&display=swap');

body {
  background: #eee;
  font-family: 'Oswald', sans-serif !important;
  min-width: 320px;
}

.btn {
  font-family: 'Oswald', sans-serif !important;
}

.auth-form {
  width: 500px;
  border-radius: 10px;
}

.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: calc(100vh - 264px);
}

.main-wrap {
  margin: 100px 0;
}

.login input {
  color: #fff;
}

.alex-khrapal {
  position: fixed;
  bottom: 20px;
  left: 20px;
  font-size: 16px;
  line-height: 18px;
  font-weight: 700;
  padding: 5px;
  background: lavender;
}

@media (max-width: 650px) {
    .auth-form {
      width: 100%;
    }

    .main-wrap {
      margin: 60px 0 80px 0;
    }

    .wrapper {
      display: block;
      height: auto;
    }
}

input:-webkit-autofill,
input:-webkit-autofill:hover,
input:-webkit-autofill:focus,
input:-webkit-autofill:active {
    -webkit-animation: autofill 0s forwards;
    animation: autofill 0s forwards;
}

@keyframes autofill {
    100% {
        background: transparent;
        color: inherit;
    }
}
</style>
