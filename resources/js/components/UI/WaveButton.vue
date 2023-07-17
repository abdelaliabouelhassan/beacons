<template>
  <button  class="button w-full " @mousedown="showRippleEffect" >
     <slot></slot>
    <span v-if="showRipple" class="ripple" :style="rippleStyle"></span>
  </button>

</template>

<style>
.button {
  position: relative;
  overflow: hidden;
}

/*  Ripple */

.ripple {
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(169, 161, 161, 0.9);
  transform: scale(0);
  position: absolute;
  opacity: 1;
}
.ripple-effect {
    animation: ripple .4s linear;
}

@keyframes ripple {
  100% {
    transform: scale(2.5);
    opacity: 0;
  }
}
</style>

<script>
export default {
  data() {
    return {
      showRipple: false,
      rippleStyle: {},
    };
  },
  mounted() {
    this.showRipple = localStorage.getItem('rippleEffect') === 'true';
    const rippleStyleString = localStorage.getItem('rippleStyle');
    if (rippleStyleString) {
      this.rippleStyle = JSON.parse(rippleStyleString);
    }
  },
  methods: {
    showRippleEffect(event) {
      this.showRipple = true;
      const button = event.currentTarget;    
        // Setup
        var target =  button.getBoundingClientRect();
        var buttonSize = target.width > target.height ? target.width : target.height;
        // remove any previous ripple containers
        var elements = document.getElementsByClassName("ripple");
        while (elements[0]) {
          elements[0].parentNode.removeChild(elements[0]);
        }

        // create the ripple container and append it to the target element
        var ripple = document.createElement("span");
        ripple.setAttribute("class", "ripple");
        button.appendChild(ripple);

        // set the ripple container to the click position and start the animation
        setTimeout(function() {
          ripple.style.width = buttonSize + "px";
          ripple.style.height = buttonSize + "px";
          ripple.style.top = event.offsetY - buttonSize / 2 + "px";
          ripple.style.left = event.offsetX - buttonSize / 2 + "px";
          ripple.setAttribute("class", "ripple ripple-effect");
        }, 100);
      },
  },
};
</script>
