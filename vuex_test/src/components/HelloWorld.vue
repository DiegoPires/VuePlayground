<template>
  <div>
    <h1>{{ count }}</h1>
    <a @click="increment">asd</a>
  </div>
</template>

<script>
import store from '@/store'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  computed: {
    count () {
      return store.state.count
    }
  },
  methods: {
    increment: function () {
      store.commit('increment')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
