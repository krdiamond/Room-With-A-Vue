<template>
  <div id="shelf-area">

    <img id="shelf"  :src="shelfImage"/>

    <div id="watering-can" class="draggable">
        <img id="titled-watering-can" v-if="canIsPouring" :src="wateringCanTiltedImage"/>
        <img id="water" v-if="canIsPouring" :src="waterImage"/>
        <img v-else :src="wateringCanImage"/>
    </div>

    <div id="planter" class="">
      <div class="planter-pour-zone"></div>
      <img :src="planterImage"/>
    </div>


  </div>
</template>


<script>
import shelfFile from "./images/shelf.png"
import interact from 'interact.js';
import wateringCanFile from "./images/watering-can.png"
import wateringCanTiltedFile from "./images/watering-can-tilted.png"
import waterFile from "./images/water.gif"
import planterFile from "./images/planter.png"

export default {
  name: 'shelf',
  data(){
    return {
      shelfImage: shelfFile,
      wateringCanImage: wateringCanFile,
      wateringCanTiltedImage: wateringCanTiltedFile,
      waterImage: waterFile,
      planterImage: planterFile,
      canIsPouring: false,
    }
  },
  mounted() {
    var shelf = document.getElementById('shelf');
    interact('.draggable')
    .draggable({
      onmove: this.dragMoveListener,
      inertia: true,
      restrict: {
        restriction: shelf,
        elementRect: { top: .90, left: 0, bottom: 1.1, right: 1 },
        endOnly: true
      },
    });
    interact('.planter-pour-zone')
    .dropzone({
      overlap: .5,
      ondrop: this.onDrop,
      ondragenter: this.dragEnter,
      ondragleave: this.dragLeave,
    })
  },
  methods: {
    dragMoveListener(event) {
      var target = event.target,
          x = (parseFloat(target.getAttribute('data-x')) || 0) + event.dx,
          y = (parseFloat(target.getAttribute('data-y')) || 0) + event.dy;
      // translate the element's CSS/Styling (so that it can move starting from the line above data positioning)
      target.style.webkitTransform = 'translate(' + x + 'px, ' + y + 'px)';
      target.style.transform = 'translate(' + x + 'px, ' + y + 'px) rotate('+ '0' + 'deg)';
      // update the posiion attributes so that it keeps moving
      target.setAttribute('data-x', x);
      target.setAttribute('data-y', y);
    },
    dragEnter() {
      this.canIsPouring = true;
    },
    dragLeave() {
      this.canIsPouring = false;
    },
    onDrop() {
      this.canIsPouring = false;
    }
  }
}
</script>

<style lang="scss" src="./shelf.scss"></style>
