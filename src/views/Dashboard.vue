<template>
  <v-stage :config="configKonva">
    <v-layer>
      <!-- <v-image :config="{
            image: image
          }"/> -->
      <v-rect :config="configOuter"></v-rect>
      <v-circle :config="configCircle1"></v-circle>
      <v-circle :config="configCircle2"></v-circle>
      <v-circle :config="configCircle3"></v-circle>
    </v-layer>
  </v-stage>
</template>

<script>
export default {
  data() {
    return {
      configKonva: {
        width: window.innerWidth,
        height: window.innerHeight
      },
      configCircle1: {
        x: 500,
        y: 300,
        radius: 7,
        fill: "red"
      },
      configCircle2: {
        x: 100,
        y: 200,
        radius: 7,
        fill: "red"
      },
      configCircle3: {
        x: 700,
        y: 500,
        radius: 7,
        fill: "red"
      },
      configOuter: {
        x: 20,
        y: 20,
        width: window.innerWidth-300,
        height: window.innerHeight-100,
        stroke: "black",
        strokeWidth: 4
      },
      // image: null
    };
  },
  // created() {
  //   const image = new window.Image();
  //   image.src = "https://konvajs.org/assets/yoda.jpg";
  //   image.onload = () => {
  //     // set image only when it is loaded
  //     this.image = image;
  //   };
  // }
};
</script>

<style>
  
</style>