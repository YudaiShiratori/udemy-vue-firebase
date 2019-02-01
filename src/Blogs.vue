<template>
  <div class="blog">
    <h2>{{ BlogTitle }}</h2>
    <button @click='changeTitle'>Change Title</button>
  </div>
</template>

<script>
export default {
  name: 'Blogs',
  data() {
    return {
      BlogTitle: 'Como estas?'
    }
  },
  methods: {
    changeTitle() {
      this.BlogTitle = 'Bien!'
    }
  },
  beforeCreate() {
    alert('beforeCreate')
  },
  created() {
    alert('created')
  },
  beforeUpdate() {
    alert('beforeUpdate')
  }
}
</script>
