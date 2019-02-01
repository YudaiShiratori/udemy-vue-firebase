<template>
  <div id="app">
    <router-view />
    <h1>{{ title }}</h1>
    <Navbar />
    <AllFriends :friends='friends' @delete ='deleteFriend'/>
    <OnlineFriends :friends='friends' />
    <Blogs />
  </div>
</template>

<script>
import Navbar from '@/components/Navbar'
import AllFriends from '@/components/AllFriends'
import OnlineFriends from '@/components/OnlineFriends'
import Blogs from '@/components/Blogs'
export default {
  name: 'App',
  components: {
    Navbar,
    AllFriends,
    OnlineFriends,
    Blogs
  },
  data () {
    return {
      title: 'Vue+Firebase',
      friends: [
        { name: 'aa', online: true },
        { name: 'bb', online: false },
        { name: 'cc', online: true },
        { name: 'dd', online: false }
      ]
    }
  },
  methods: {
    deletefriend (payload) {
      console.log(payload.friend)
      // this.friends = this.friends.filter(friend => {
      //   return friend.name !== payload.name
      // })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
