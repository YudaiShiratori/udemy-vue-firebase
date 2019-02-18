<template>
  <nav>menu
    <ul>
      <li><router-link to="/">HOME</router-link></li>
      <li><router-link :to="{ name: 'About' }">ABOUT</router-link></li>
      <li><a href="">Contact</a></li>
    </ul>
    <h2>USER PROFILES</h2>
    <ul>
      <li v-for="(id, index) in userIds" :key="index">
        <router-link :to="{ name: 'ViewProfile', params: { user_id: id }}">
          <span>PROFILE {{ id }}</span>
        </router-link>
      </li>
    </ul>
    <h2>Navigation Control</h2>
    <ul>
      <li><button @click="goBack">Back</button></li>
      <li><button @click="goHome">redirect to home</button></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data () {
    return {
      userIds: ['1', '2', '3', '4']
    }
  },
  methods: {
    goHome() {
      this.$router.push({name: 'Home'})
    },
    goBack() {
      this.$router.go(-1)
    }
  }
}
</script>

<style scoped>
nav {
  text-align: center;
}
nav ul{
  padding: 0
}
nav li{
  display: inline-block;
  list-style-type: none;
  margin: 10px;
}
a {
  color: #42b983
}

a .router-link-active{
  color: purple;
}
</style>

/* eslint-disable */
