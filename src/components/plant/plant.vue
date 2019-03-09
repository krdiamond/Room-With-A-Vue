<template>

  <div id="plant">


      <img id="sprout" :src="sproutImage"/>
      <img id="planter" :src="planterImage"/>

  </div>
</template>

<script>

import sproutFile from "./images/sprout.png"
import planterFile from "./images/planter.png"

export default {
  name: 'plant',
  data(){
    return {
      sproutImage: sproutFile,
      planterImage: planterFile,
    }
  }
}
</script>

<style lang="scss" src="./plant.scss"></style>
