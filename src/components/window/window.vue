<template>
  <div id="window-open-or-closed">

    <div id="window" v-bind:class="{click_through: windowIsOpened}">

        <img id="closed-window"
              v-on:click="windowIsOpened = !windowIsOpened"
              v-bind:class="{ hide: windowIsOpened}"
              img :src="closedWindowImage">

        <img id="open-window"
             v-on:click="windowIsOpened = !windowIsOpened"
             v-bind:class="{ hide: !windowIsOpened}"
             img :src="openWindowImage"/>
    </div>


     <div id="left-open-window" v-on:click="windowIsOpened = !windowIsOpened" ></div>
     <div id="right-open-window" v-on:click="windowIsOpened = !windowIsOpened"></div>

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
