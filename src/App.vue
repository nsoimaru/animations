<template>
<div>
  <button type="button" @click="flag = !flag">Togle</button>

  <!-- <transition name="fade" mode="out-in">  
    <h2 v-if="flag" key="main">Hello world</h2>
    <h2 v-else key="secondary">Anoteher Hello</h2>
  </transition> -->

  <!-- <transition name="zoom" type="animation" appear>
    <h2 v-if="flag">Hello!</h2>  
  </transition> -->

  <transition
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter"
    @before-leave="beforeLeave"
    @leave="leave"
    @after-leave="afterLeave"
  >
    <h2 v-if="flag">Hello!</h2>
  </transition>
</div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      flag: true,
    }
  },
  methods: {
    beforeEnter(el) {
    console.log('beforeEnter element was triggered!', el)
    },
    enter(el, done) {
      console.log('enter element was triggered!', el)
      done();
    },
    afterEnter(el) {
      console.log('afterEnter element was triggered!', el)
    },
    beforeLeave(el) {
      console.log('beforeLeave element was triggered!', el)
    },
    leave(el, done) {
      console.log('leave element was triggered!', el)
      done();
    },
    afterLeave(el) {
      console.log('afterLeave element was triggered!', el)
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
  transition: all 1s linear;
}

.zoom-leave-active {
  animation: zoom-out 1s linear forwards;
  transition: all 1s linear;
}

.zoom-enter-from {
  opacity: 0;
}

.zoom-leave-to {
  opacity: 0;
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