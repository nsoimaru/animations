<template>
<div>
  <button type="button" @click="flag = !flag">Togle</button>

  <transition name="fade" mode="out-in">  
    <h2 v-if="flag" key="main">Hello world</h2>
    <h2 v-else key="secondary">Anoteher Hello</h2>
  </transition>
</div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      flag: false,
    }
  }
}
</script>

<style>
.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 3s linear;
}

.fade-leave-to {
  transition: all 3s linear;
  opacity: 0;
}
</style>