<template>
  <v-stage :config="configKonva">
    <v-layer>
      <!-- <v-image :config="{
            image: image
          }"/> -->
      <v-rect :config="configOuter"></v-rect>
      <v-rect :config="configArea1"></v-rect>
      <v-rect :config="configArea2"></v-rect>
      <v-rect :config="configArea3"></v-rect>
      <v-rect :config="configArea4"></v-rect>
      <v-rect :config="configArea5"></v-rect>
      <v-rect :config="configArea6"></v-rect>
      <v-rect :config="configArea7"></v-rect>
      <v-circle :config="configCircle1"></v-circle>
      <v-circle :config="configCircle2"></v-circle>
      <v-circle :config="configCircle3"></v-circle>
    </v-layer>
  </v-stage>
</template>

<script>
export default {
  name: 'dashboard',
  data() {
    return {
      configKonva: {
        width: window.innerWidth,
        height: window.innerHeight
      },
      configCircle1: {
        x: 75,
        y: 75,
        radius: 7,
        fill: "salmon"
      },
      configCircle2: {
        x: 120,
        y: 75,
        radius: 7,
        fill: "salmon"
      },
      configCircle3: {
        x: 700,
        y: 500,
        radius: 7,
        fill: "salmon"
      },
      configOuter: {
        x: 20,
        y: 20,
        width: 1045,
        height: 555,
        fill: "lightyellow",
        stroke: "black",
        strokeWidth: 4
      },
      configArea1: {
        x: 45,
        y: 45,
        width: 315,
        height: 180,
        fill: "palegreen"
      },
      configArea2: {
        x: 385,
        y: 45,
        width: 315,
        height: 180,
        fill: "palegreen"
      },
      configArea3: {
        x: 725,
        y: 45,
        width: 315,
        height: 180,
        fill: "palegreen"
      },
      configArea4: {
        x: 45,
        y: 250,
        width: 230,
        height: 300,
        fill: "palegreen"
      },
      configArea5: {
        x: 300,
        y: 250,
        width: 230,
        height: 300,
        fill: "palegreen"
      },
      configArea6: {
        x: 555,
        y: 250,
        width: 230,
        height: 300,
        fill: "palegreen"
      },
      configArea7: {
        x: 810,
        y: 250,
        width: 230,
        height: 300,
        fill: "palegreen"
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