<template>

  <div id="the-view">


    <img id="pool" :src="poolImage" v-if="itsDayTime"/>
    <img id="pool" :src="nightPoolImage" v-if="!itsDayTime"/>

    <img id="rain" :src="rainImage" v-if="itsRaining"/>

    <div id="clouds" v-if="itsDayTime">
         <img id="cloud1" :src="cloudImage" v-on:click="itsRaining = !itsRaining"/>
         <img id="cloud2" :src="cloudImage" v-on:click="itsRaining = !itsRaining"/>
         <img id="cloud3" :src="cloudImage" v-on:click="itsRaining = !itsRaining"/>
    </div>

  </div>
</template>

<script>
import poolFile from "./images/pool.jpg"
import nightPoolFile from "./images/pool_night.jpg"
import cloudFile from "./images/cloud.png"
import rainFile from "./images/raining.gif"

export default {
  name: 'the-view',
  data(){
    return {
      poolImage: poolFile,
      nightPoolImage: nightPoolFile,
      cloudImage: cloudFile,
      rainImage: rainFile,
      itsRaining: false,
      counter: 1,
      itsDayTime: true,
    }
  },
  watch: {
    counter: function () {
      if (this.counter % 10 == 0 ) {
        this.itsDayTime = !this.itsDayTime;
      }
    }
  },
  // created () {
  //   setInterval(() => this.counter += 1, 2000);
  // }
}
</script>
