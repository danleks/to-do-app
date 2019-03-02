<template>
  <div id="app">
    <app-header :task="task" />
    <transition
      name="fade"
      leave-active-class="fadeOut"
    >
      <app-content v-if="!task" />
    </transition>
      <transition
      name="slide"
      enter-active-class="slideIn"
    >
      <app-task v-if="task" />
      </transition>
    <app-controls :tasks="tasks" v-if="!task" @add-task="addTask"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Content from './components/Content.vue';
import Controls from './components/Controls.vue';
import Task from './components/Task.vue';




export default {
  name: 'app',
  data() {
    return {
      tasks: [],
      task: false,
    }
  },

  methods: {
    addTask(e) {
      this.task = e;
    }
  },

  components: {
    'app-header': Header,
    'app-content': Content,
    'app-controls': Controls,
    'app-task': Task,
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Mali:300,400,500,600,700');

// GLOBAL RESET
html {
  box-sizing: border-box;
  font-size: 62.5%;
}
*, *:before, *:after {
  box-sizing: inherit;
  padding: 0;
  margin: 0;
}

#app {
  font-family: 'Mali', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

  :root {
    // BASIC COLORS
    --header-color: #110025;
    --header-color-t: #FF0046;
    --content-color: #FF0046;
    --content-color-t: #110025;
    --text-color: #fff;

    // BASIC DIMENSIONS
    --header-height: 20vh;
    --content-height: calc(100vh - var(--header-height));
  }


  //ANIMATIONS
  @keyframes slideIn {
    0% {transform: translateX(50rem); opacity: 0;}
    100% {transform: translateX(0); opacity: 1;}
  }

  @keyframes fadeOut {
    0% {opacity: 1;}
    100% {opacity: 0;}
  }

  .slideIn {
    animation: slideIn .3s ease-out;
  }

  .fadeOut {
    animation: fadeOut .2s ease-in;
  }



</style>
