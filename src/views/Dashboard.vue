<template>
  <v-stage :config="configKonva">
    <v-layer>
      <!-- <v-image :config="{
            image: image
      }"/>-->
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
  name: "dashboard",
  data() {
    return {
      configKonva: {
        width: window.innerWidth,
        height: window.innerHeight-60
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
        y: 400,
        radius: 7,
        fill: "salmon"
      },
      configOuter: {
        x: 20,
        y: 20,
        width: 836,
        height: 444,
        fill: "lightyellow",
        stroke: "black",
        strokeWidth: 4
      },
      configArea1: {
        x: 40,
        y: 40,
        width: 252,
        height: 144,
        fill: "palegreen"
      },
      configArea2: {
        x: 312,
        y: 40,
        width: 252,
        height: 144,
        fill: "palegreen"
      },
      configArea3: {
        x: 584,
        y: 40,
        width: 252,
        height: 144,
        fill: "palegreen"
      },
      configArea4: {
        x: 40,
        y: 204,
        width: 184,
        height: 240,
        fill: "palegreen"
      },
      configArea5: {
        x: 244,
        y: 204,
        width: 184,
        height: 240,
        fill: "palegreen"
      },
      configArea6: {
        x: 448,
        y: 204,
        width: 184,
        height: 240,
        fill: "palegreen"
      },
      configArea7: {
        x: 652,
        y: 204,
        width: 184,
        height: 240,
        fill: "palegreen"
      }
      // image: null
    };
  },

  created() {
    this.id = console.log(this.$route.params.id);
  }
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