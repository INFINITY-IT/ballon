<template>
  <svg
      @click="startScissors"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 100 100"
      width="300"
      height="300"
      aria-labelledby="scissors"
      role="presentation"
  >
    <title id="scissors" lang="en">Scissors Animated Icon</title>
    <path id="bk" fill="#fff" d="M0 0h100v100H0z"/>
    <g ref="leftscissor">
      <path d="M7.246 3.255a6.046 6.046 0 0 0-.198 2.597 5.988 5.988 0 0 0 7.672 4.892c-.674 2.215-2.642 3.926-4.973 4.21a5.994 5.994 0 0 1-5.248-1.977C3.347 11.673 2.83 9.99 3.042 8.238c.284-2.335 1.992-4.307 4.204-4.982zM8.985 1a8.15 8.15 0 0 0-1.104.075c-3.543.48-6.388 3.364-6.82 6.92C.469 12.862 4.245 17 8.985 17c.33 0 .665-.02 1.003-.062 3.549-.433 6.428-3.283 6.907-6.833.052-.383.076-.761.075-1.134-.002-.583-.482-.972-.996-.972a1.02 1.02 0 0 0-.614.207 3.96 3.96 0 0 1-2.383.793c-.188 0-.38-.013-.574-.04-1.732-.242-3.137-1.649-3.378-3.385a3.997 3.997 0 0 1 .751-2.963c.415-.657.025-1.609-.764-1.612h-.028z"/>

    </g>
    <g ref="rightscissor">

    </g>
  </svg>
</template>

<script>
import gsap from 'gsap'

export default {
  props: {
    iconName: {
      type: String,
      default: 'box'
    },
    width: {
      type: [Number, String],
      default: 18
    },
    height: {
      type: [Number, String],
      default: 18
    },
    iconColor: {
      type: String,
      default: 'currentColor'
    }
  },
  methods: {
    startScissors() {
      //this.scissorAnim(this.$refs.rightscissor, 30)
      //this.scissorAnim(this.$refs.leftscissor, -30)

      var tl = gsap.timeline({
        onComplete: this.testIt
      });
//sequenced one-after-the-other
      tl.to(this.$refs.leftscissor, {duration: 2, y: 100});
      tl.to(this.$refs.leftscissor, {duration: 2, y: -100});

      tl.to(this.$refs.leftscissor, {duration: 2, y: 80});
      tl.to(this.$refs.leftscissor, {duration: 2, y: -80});

      tl.to(this.$refs.leftscissor, {duration: 2, y: 60});
      tl.to(this.$refs.leftscissor, {duration: 2, y: -60});
    },
    testIt(){
      return;
      var tl = gsap.timeline({
        onComplete: this.testIt
      });
//sequenced one-after-the-other
      tl.to(this.$refs.leftscissor, {duration: 1, x: 90});
    },
    scissorAnim(el, rot) {
      TweenMax.to(el, 0.25, {
        rotation: rot,
        repeat: 3,
        yoyo: true,
        svgOrigin: '50 45',
        ease: Sine.easeInOut
      })
    }
  }
}
</script>