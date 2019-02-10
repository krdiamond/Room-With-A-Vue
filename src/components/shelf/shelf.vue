<template>

  <div id="shelf-area">


    <img id="shelf" class="drop-zone" :src="shelfImage"/>

    <img id="watering-can" class="draggable" :src="wateringCanImage"/>

  </div>
</template>


<script>
import shelfFile from "./images/shelf.png"
import interact from 'interact.js';
import wateringCanFile from "./images/watering-can.png"

export default {
  name: 'shelf',
  data(){
    return {
      shelfImage: shelfFile,
      wateringCanImage: wateringCanFile,
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
    interact('.drop-zone')
    .dropzone({
      overlap: 0,
      ondrop: this.onDropListener,
    })
  },
  methods: {
    dragMoveListener (event) {
      var target = event.target,
          x = (parseFloat(target.getAttribute('data-x')) || 0) + event.dx,
          y = (parseFloat(target.getAttribute('data-y')) || 0) + event.dy;
      // translate the element's CSS/Styling (tilts watering can)
      target.style.webkitTransform = 'translate(' + x + 'px, ' + y + 'px)';
      target.style.transform = 'translate(' + x + 'px, ' + y + 'px) rotate('+ '-60' + 'deg)';
      // update the posiion attributes
      target.setAttribute('data-x', x);
      target.setAttribute('data-y', y);
    },
    onDropListener (event) {
      var target = event.relatedTarget,
          x = (parseFloat(target.getAttribute('data-x')) || 0),
          y = (parseFloat(target.getAttribute('data-y')) || 0);
          //untilts watering can
     target.style.transform = 'translate(' + x + 'px, ' + y + 'px) rotate('+ '0' + 'deg)';

    }
  }
}
</script>



interact(element)
  .draggable({
    snap: {
      targets: [
        interact.createSnapGrid({ x: 30, y: 30 })
      ],
      range: Infinity,
      relativePoints: [ { x: 0, y: 0 } ]
    },
    inertia: true,
    restrict: {
      restriction: element.parentNode,
      elementRect: { top: 0, left: 0, bottom: 1, right: 1 },
      endOnly: true
    }
  })
  .on('dragmove', function (event) {
    x += event.dx;
    y += event.dy;

    event.target.style.webkitTransform =
    event.target.style.transform =
        'translate(' + x + 'px, ' + y + 'px)';
  });
