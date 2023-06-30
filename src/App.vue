<template>
  <div id="app">
    <EditContactForm :id="1"/>
    <ContactForm/>
    <UserList/>
  </div>
</template>

<script>
import EditContactForm from './components/EditContactForm.vue';
import ContactForm from './components/ContactForm.vue';
import UserList from './components/UserList.vue';

export default {
  name: 'App',
  components: {
    EditContactForm,
    ContactForm,
    UserList
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
