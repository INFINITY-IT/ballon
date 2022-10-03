<template>
  <div class="box">
    <div ref="sphere" class="sphere"></div>
  </div>
  <div ref="dot" class="dot"></div>
</template>
<script>
import { gsap } from "gsap";

import { MotionPathPlugin } from 'gsap/MotionPathPlugin';
import { Draggable } from 'gsap/Draggable';
gsap.registerPlugin(MotionPathPlugin,Draggable);

export default {
  mounted() {
    let sphere = this.$refs.sphere;
    Draggable.create([sphere], {onRelease: this.bounceSphere, bounds: window});
  },
  methods:{
    bounceSphere(){
      let sphere = this.$refs.sphere, dot = this.$refs.dot;

      let DOMRect = sphere.getBoundingClientRect();
      let DOMRectBottom = dot.getBoundingClientRect();

      this.yCoordinate = DOMRectBottom.y;

      const timeline = new gsap.timeline({repeat: -1,yoyo: true});

      timeline.to(sphere, {
        duration: 1,
        repeatDelay: 0.5,
        y: "=" + DOMRectBottom.y,
        ease: "power1.inOut",
        overwrite: true,
      });

      setTimeout(() => {
        timeline.pause();
      }, 7000);
    },
  }
}
</script>