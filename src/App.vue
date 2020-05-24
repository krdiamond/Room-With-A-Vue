<template>
  <div id="RoomWithaView" class="room-with-a-vue" >

      <TheVueOutside/>
      <TheVueInside/>

  </div>
</template>

<script>
 import TheVueInside from './components/the-vue-inside/the-view-inside__component.vue'
 import TheVueOutside from './components/the-vue-outside/the-view-outside__component.vue'


  export default {
    name: 'app',
    components: {   //component must be called here in addition to import
      TheVueInside,
      TheVueOutside,
    }
  }
</script>


<style lang="scss" src="./app.scss"></style>
