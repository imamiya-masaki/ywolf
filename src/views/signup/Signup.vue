<template>
  <div class="signup">
    <h2>Sign up</h2>
    <input type="text" placeholder="Username" v-model="username">
    <input type="password" placeholder="Password" v-model="password">
    <button @click="signUp">Register</button>
    <p>Do you have an account?
      <router-link to="/signin">sign in now!!</router-link>
    </p>
  </div>
</template>

<script>
import firebase from 'firebase'

export default {
  name: 'Signup',
  data() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    signUp() {
      firebase.auth().createUserWithEmailAndPassword(this.username, this.password)
        .then((user) => {
          console.log('Create account:', user.email)
        })
        .catch((error) => {
          console.log('usercreate:err', error.message)
        })
    },
  },
}
</script>

<style scoped>
 /* 省略 */
</style>
