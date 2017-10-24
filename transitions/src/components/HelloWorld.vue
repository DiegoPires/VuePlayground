<template>
  <div>
    
    <nav class="level">
      <p class="level-item">
        <a @click="up">up</a>
      </p>
    </nav>

    <article class="media">
      
      <div class="media-left" @click="previous" :key="1">
        &lt;
      </div>
      <div class="media-content">
        <div class="content">
          <p>
            <strong>{{ msg }}</strong> <small>@johnsmith</small> <small>31m</small>
            <br>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ornare magna eros, eu pellentesque tortor vestibulum ut. Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.
          </p>
        </div>
        <nav class="level is-mobile">
          <div class="level-left">
            <a class="level-item">
              <span class="icon is-small"><i class="fa fa-reply"></i></span>
            </a>
            <a class="level-item">
              <span class="icon is-small"><i class="fa fa-retweet"></i></span>
            </a>
            <a class="level-item">
              <span class="icon is-small"><i class="fa fa-heart"></i></span>
            </a>
          </div>
        </nav>
      </div>
      <div @click="next" class="media-right">
        &gt;
      </div>
    </article>

    <nav class="level">
      <p class="level-item">
        <a @click="down">down</a>
      </p>
    </nav>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App ' + this.$route.params.stuff
    }
  },
  watch: {
    '$route' (to, from) {
      console.log(to)
    }
  },
  methods: {
    next: function () {
      this.naviguer('next')
    },
    previous: function () {
      this.naviguer('previous')
    },
    up: function () {
      this.naviguer('up')
    },
    down: function () {
      this.naviguer('down')
    },
    naviguer: function (ou) {
      this.$emit(ou)
      this.$router.push({ name: 'Hello', params: { 'stuff': ou } })
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
