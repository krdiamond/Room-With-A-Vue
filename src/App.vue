<template>
  <div id="app" >
    <div id="the-vue-container" >

      <Window/>
      <theView/>

    </div>
  </div>
</template>

<script>
 import Window from './components/window/window.vue'
 import theView from './components/the-view/the-view.vue'


  export default {
    name: 'app',
    components: {   //component must be called here in addition to import
      Window,
      theView,
    }
  }
</script>


<style lang="scss" src="./app.scss"></style>
