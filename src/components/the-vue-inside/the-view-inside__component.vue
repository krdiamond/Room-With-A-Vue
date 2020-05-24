<template>
  <div class="the-vue-inside">

    <div class="window-closed" v-bind:class="{click_through: windowIsOpened}">

        <img v-on:click="windowIsOpened = !windowIsOpened"
              v-bind:class="{ hide: windowIsOpened}"
              img :src="closedWindowImage">

        <img v-on:click="windowIsOpened = !windowIsOpened"
             v-bind:class="{ hide: !windowIsOpened}"
             img :src="openWindowImage"/>
    </div>


     <div class="window-open window-open__left" v-on:click="windowIsOpened = !windowIsOpened" ></div>
     <div class="window-open window-open__right" v-on:click="windowIsOpened = !windowIsOpened"></div>

     <div class="planter-pour-zone"></div>

    <Shelf/>
  </div>

</template>


<script>

import closedWindowFile from "./images/window-closed.png"
import openWindowFile from "./images/window-open.png"
import Shelf from '../shelf/shelf.vue'




export default {
  name: 'window',
  components: {   //component must be called here in addition to import
    Shelf,
  },
  data(){
    return {
      openWindowImage: openWindowFile,
      closedWindowImage: closedWindowFile,
      windowIsOpened: false,
    }
  }
}
</script>



<!-- rainsFor5Seconds() {

 } -->
