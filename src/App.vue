<template>
  <div id="app">
    <app-header :task="task" :tasks="tasks" />
      <app-content @delete-task="deleteTask" :tasks="tasks" v-if="!task" />
      <app-task :tasks="tasks" v-if="task" />
    <app-controls
    @add-task="addTask"
    @delete-item="deleteItem"
    @delete-all="deleteAll"
    :tasks="tasks"
    v-if="!task" />
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
      id: null,
    }
  },

  methods: {
    addTask(e) {
      this.task = e;
    },
    deleteItem() {
      this.tasks.splice(this.tasks.length-1, 1);
    },
    deleteAll(){
      this.tasks = [];
    },
    deleteTask(e) {
      let itemIndex = this.tasks.indexOf(e);
      this.tasks.splice(itemIndex, 1);
    }
  },

  components: {
    'app-header': Header,
    'app-content': Content,
    'app-controls': Controls,
    'app-task': Task,
  },

  mounted() {
    this.$root.$on('add-task', (task, boolean) => {
      this.task = boolean;
      this.tasks.push(task);
    })
     this.$root.$on('cancel', (boolean) => {
      this.task = boolean;
    })
  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Mali:300,400,500,600,700');

// GLOBAL RESET
html {
  box-sizing: border-box;
  font-size: 62.5%;
  overflow: hidden;
}
*, *:before, *:after {
  box-sizing: inherit;
  padding: 0;
  margin: 0;
}

#app {
  position: relative;
  max-width: 768px;
  margin: auto;
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
    --task-color: #190036;

    // BASIC DIMENSIONS
    --header-height: 20vh;
    --content-height: calc(100vh - var(--header-height));

      @media(min-width: 768px) {
        --content-height: calc(100vh - var(--header-height) - 5vh);
      }
  }


  //ANIMATIONS
//   @keyframes zoomIn {
//     0% {transform: scale(.5); opacity: 0;}
//     100% {transform: scale(1);}
//   }

//  @keyframes fadeOut {
//     0% {opacity: 0;}
//     100% {opacity: 0;}
//   }

//   .zoomIn {
//     animation: zoomIn .1s ease-in;
//   }

//   .fadeOut {
//     animation: fadeOut .1s ease-in;
//   }




</style>
