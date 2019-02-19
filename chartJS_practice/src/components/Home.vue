<template>
　 <div id="home">
　 <h1>{{ msg }}</h1>
   <input v-model="message">
   <p>Message is: {{ message }}</p>
　 <button @click="googleLogin">Google アカウントでログイン </button>
　 </div>
　</template>
　<script>
　export default {
　 name: 'home',
　 data () {
　 return {
　 msg: 'Welcome to MyMarkdown',
   message: '123'
　 }
},
　 methods: {
　 googleLogin: function() {
　 firebase.auth().signInWithRedirect(new firebase.auth.GoogleAuthProvider());
　 }
　 }
 }
　</script>