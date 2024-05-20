/**
* FILEPATH: /C:/Users/silva/OneDrive/Desktop/Projects/VueJS/Vue JS Projects/animations-1/src/App.vue
*
* @name App
* @description The main component of the Vue application.
* @component
*
* @template
* Contains the HTML template for the component.
* It includes a button that toggles the flag value and a transition effect for the h2 element.
*
* @script
* Contains the JavaScript code for the component.
* It exports an object with the component's name and data.
* The data object includes a flag property that controls the visibility of the h2 element.
*
* @style
* Contains the CSS styles for the component.
* It includes styles for the h2 element and the transition animations.
*/
<template>
  <button type="button" @click="flag = !flag">Toggle</button>
  <!-- <transition name="fade" mode="out-in">
    <h2 v-if ="flag" key="main">First Test Application!</h2>
    <h2 v-else key="secondary">Second Test Application!</h2>
  </transition> -->


  <!-- <transition name="zoom" type="animation" appear="true">
    <h2 v-if="flag">ZOOM EFFECT!</h2>
  </transition> -->

<transition 
@before-enter="beforeEnter" 
@enter="enter" 
@after-enter="afterEnter" 
@before-leave="beforeLeave" 
@leave="leave" 
@after-leave="afterLeave"
>
  <h2 v-if="flag">ZOOM EFFECT!</h2>
</transition>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      flag: true
    }
  },
  methods: {
    beforeEnter(el) {
      console.log('beforeEnter');
      el.style.transform = 'scale(0)'
    },
    enter(el) {
      console.log('enter');
      el.style.transform = 'scale(1)'
    },
    afterEnter(el) {
      console.log('afterEnter');
      el.style.transform = 'scale(1)'
    },
    beforeLeave(el) {
      console.log('beforeLeave');
      el.style.transform = 'scale(1)'
    },
    leave(el) {
      console.log('leave');
      el.style.transform = 'scale(0)'
    },
    afterLeave(el) {
      console.log('afterLeave');
      el.style.transform = 'scale(0)' 
    }
    }   
}
</script>


<style>
h2 {
  width: 400px;
  padding: 20px;
  margin: 20px;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s linear;
}

.fade-leave-to {
  transition: all 1s linear;
  opacity: 0;
}

.zoom-enter-active {
  animation: zoom-in 1s linear forwards;
}

.zoom-leave-active {
  animation: zoom-out 1s linear forwards;
}

@keyframes zoom-in {
  from {
    transform: scale(0, 0);
  }

  to {
    transform: scale(1, 1);
  }
}

@keyframes zoom-out {
  from {
    transform: scale(1, 1);
  }

  to {
    transform: scale(0, 0);
  }
}
</style>