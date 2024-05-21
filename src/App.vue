/**
FILEPATH: /C:/Users/silva/OneDrive/Desktop/Projects/VueJS/Vue JS Projects/animations-1/src/App.vue
** name App
* @escription The main component of the Vue application.
* @cmponent
*
* @emlate
* Contans the HTML template for the component.
* It incudes a button that toggles the flag value and a transition effect for the h2 element.
*
* @scrit
Contains he JavaScript code for the component.
* It exportsan object with the component's name and data.
* The data obect includes a flag property that controls the visibility of the h2 element.
*
* @style
* Cntins the CS styles for the component.
* It includes styes for the h2 element and the transition animations.
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

  <!-- <transition 
  @before-enter="beforeEnter" 
  @enter="enter" 
  @after-enter="afterEnter" 
  @before-leave="beforeLeave"
  @leave="leave" 
  @after-leave="afterLeave"
    :css="true"
  name="fade"
  >

    <h2 v-if="flag">ZOOM!</h2>
  </transition> -->

  <button @click="addItem">Add</button>

  <ul>
    <transition-group name="fade" 
      enter-active-class="animate__animated animate__flipInX"
      leave-active-class="animate__animated animate__flipOutX"
    >

      <li v-for="( number, index) in numbers" :key="number" @click="remove(index)">
        {{ number }}
      </li>
    </transition-group>

  </ul>
</template>

<script>

/**
 * Vue component representing the main application.
 *
 * @name App
 * @component
 */
export default {
  name: 'App',
  data() {
    return {
      flag: true,
      numbers: [1, 2, 3, 4, 5]
    }
  },
  methods: {
    addItem() {
      const num = Math.floor(Math.random() * 100 + 1)
      const index = Math.floor(Math.random() * this.numbers.length)
      this.numbers.splice(index, 0, num)
    },
    remove(index) {
      this.numbers.splice(index, 1)
    },
    /**
     * Lifecycle hook called before the element is inserted into the DOM.
     *
     * @param {HTMLElement} el - The element being inserted.
     */
    beforeEnter(el) {
      console.log('beforeEnter', el);
      el.style.transform = 'scale(0)'
    },
    /**
     * Lifecycle hook called when the element is inserted into the DOM.
     *
     * @param {HTMLElement} el - The inserted element.
     */
    enter(el) {
      console.log('enter', el);
      // const animation = el.animate([
      //   { transform: 'scale3d(0,0,0)' },
      //   { transform: 'scale3d(1,1,1)' }
      // ], {
      //   duration: 1000,
      // });
      // animation.onfinish = () => {
      //   done();
      // };
    },
    /**
     * Lifecycle hook called after the element is inserted into the DOM.
     *
     * @param {HTMLElement} el - The inserted element.
     */
    afterEnter(el) {
      console.log('afterEnter', el);
      el.style.transform = 'scale(1)'
    },
    /**
     * Lifecycle hook called before the element is removed from the DOM.
     *
     * @param {HTMLElement} el - The element being removed.
     */
    beforeLeave(el) {
      console.log('beforeLeave', el);
      el.style.transform = 'scale(1)'
    },
    /**
     * Lifecycle hook called when the element is removed from the DOM.
     *
     * @param {HTMLElement} el - The removed element.
     */
    leave(el) {
      console.log('leave', el);
      // const animation = el.animate([{}, {
      //   transform: 'scale3d(0,0,0)'
      // }], {
      //   duration: 1000,
      // })
      // animation.onfinish = () => {
      //   done()
      // }
    },
    /**
     * Lifecycle hook called after the element is removed from the DOM.
     *
     * @param {HTMLElement} el - The removed element.
     */
    afterLeave(el) {
      console.log('afterLeave', el);
      el.style.transform = 'scale(0)'
    }
  }
}
</script>


<style>
.animate__flipoutX {
  position: absolute;
}

.animate__animated{
  animation-duration: 1.5s;
}

li {
  font-size: 22px;
  cursor: pointer;
}

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

.fade-move {
  transition: 1s linear;
}

.fade-leave-active {
  position: absolute;
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