<template>
  <div class="blog">
    <h2>{{ BlogTitle }}</h2>
    <button @click='changeTitle'>Change Title</button>
    <h3>BLOGS</h3>
    <input type="text" v-model="searchTerm">
    <div v-for="post in filteredPosts" :key="post.id">
      <h3>{{ post.title }}</h3>
      <p>{{ post.body | snippet }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Blogs',
  data() {
    return {
      BlogTitle: 'Como estas?',
      posts: [],
      searchTerm: ''
    }
  },
  methods: {
    changeTitle() {
      this.BlogTitle = 'Bien!'
    }
  },
  /* eslint-disable */
  created() {
    axios.get('https://jsonplaceholder.typicode.com/posts')
    .then(response => {
      console.log(response)
      this.posts = response.data
    }).catch(err => {
        console.log(err)
      })
  },
  //computedは元の値は変えない
  computed: { 
    filteredPosts(){
      return this.posts.filter(post => {
        post.title.match(this.searchTerm)
      })
    }
  }
  // beforeCreate() {
  //   alert('beforeCreate')
  // },
  // created() {
  //   alert('created')
  // },
  // beforeUpdate() {
  //   alert('beforeUpdate')
  // }

}
</script>
