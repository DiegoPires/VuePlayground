<template>
  
  
<section class="hero is-info is-fullheight">
  <div class="hero-head">
    <nav class="navbar">
      <div class="container">
        <div class="navbar-brand">
          <a class="navbar-item">
            <img src="https://bulma.io/images/bulma-type-white.png" alt="Logo">
          </a>
          <span class="navbar-burger burger" data-target="navbarMenuHeroB">
            <span></span>
            <span></span>
            <span></span>
          </span>
        </div>
        <div id="navbarMenuHeroB" class="navbar-menu">
          <div class="navbar-end">
            <a class="navbar-item is-active">
              Home
            </a>
            <a class="navbar-item">
              Examples
            </a>
            <a class="navbar-item">
              Documentation
            </a>
          </div>
        </div>
      </div>
    </nav>
  </div>

  <div class="hero-body">
    <div class="container has-text-centered">
       
      <transition
        v-on:before-enter="beforeEnter"
        v-on:after-enter="afterEnter"
        v-on:before-leave="beforeLeave"
        v-on:after-leave="afterLeave"
        transition-mode="out-in">
        <router-view 
          :key="key"
          v-on:up="up"
          v-on:down="down"
          v-on:next="next"
          v-on:previous="previous" />
      </transition> 

    </div>
  </div>

</section>
   
  
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      transition: {
        in: 'fadeInLeftBig',
        out: 'fadeOutRightBig'
      }
    }
  },
  methods: {
    beforeEnter: function (el) {
      el.className = 'animated ' + this.transition.in
    },
    afterEnter: function (el) {
      el.className = ''
    },
    beforeLeave: function (el) {
      el.className = 'animated position_abs ' + this.transition.out
    },
    afterLeave: function (el) {
      el.className = ''
    },
    up: function () {
      this.transition.in = 'fadeInUpBig'
      this.transition.out = 'fadeOutUpBig'
    },
    down: function () {
      this.transition.in = 'fadeInDownBig'
      this.transition.out = 'fadeOutDownBig'
    },
    next: function () {
      this.transition.in = 'fadeInLeftBig'
      this.transition.out = 'fadeOutRightBig'
    },
    previous: function () {
      this.transition.in = 'fadeInRightBig'
      this.transition.out = 'fadeOutLeftBig'
    }
  },
  computed: {
    key () {
      return this.$route.params.stuff !== undefined
        ? this.$route.params.stuff
        : this.$route
    }
  }
}
</script>

<style>

@import "https://cdnjs.cloudflare.com/ajax/libs/bulma/0.6.0/css/bulma.css";
@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.2/animate.min.css";

.position_abs {
  position: absolute;
}

</style>
