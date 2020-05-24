<template>

  <div class="planter">

      <img class="sprout" :src="sproutImage"/>
      <img class="plant" :src="planterImage"/>

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
