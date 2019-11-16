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
      <v-rect
        v-for="area in configAreas"
        :config="area"
        v-bind:key="area.id"
      ></v-rect>

      <v-text
        v-for="text in configTextAreas"
        :config="{
          text: text.text,
          x: text.x,
          y: text.y,
          fontSize: 18,
          width: 700,
          align: center,
          fill: 'gray',
          fontStyle: 'bold'
        }"
        v-bind:key="text.id + 10"
      >
      </v-text>

      <!-- <v-circle :config="configCircles"></v-circle> -->
      <v-circle
        v-for="circle in configCircles"
        :config="circle"
        v-bind:key="circle.id + 20"
      ></v-circle>
      <!-- <v-circle :config="configCircle1"></v-circle>
      <v-circle :config="configCircle2"></v-circle>
      <v-circle :config="configCircle3"></v-circle> -->
      <v-circle :config="configCirclePusat"></v-circle>
    </v-layer>
  </v-stage>
</template>

<script>
export default {
  name: "dashboard",
  data() {
    return {
      colorsArea: [
        "lightsalmon",
        "palegreen",
        "lightcoral",
        "greenyellow",
        "coral",
        "hotpink",
        "LightSkyBlue"
      ],
      colorsVehicle: [
        "lightsalmon",
        "palegreen",
        "lightcoral",
        "greenyellow",
        "coral",
        "hotpink",
        "LightSkyBlue"
      ],
      configKonva: {
        width: window.innerWidth,
        height: window.innerHeight - 60
      },
      configCircles: [],
      configCircle1: {
        x: 75,
        y: 75,
        radius: 7,
        fill: "salmon",
        stroke: "black",
        strokeWidth: 1
      },
      configCircle2: {
        x: 120,
        y: 75,
        radius: 7,
        fill: "salmon",
        stroke: "black",
        strokeWidth: 1
      },
      configCircle3: {
        x: 700,
        y: 400,
        radius: 7,
        fill: "salmon",
        stroke: "black",
        strokeWidth: 1
      },
      configCirclePusat: {
        x: 250,
        y: 75,
        radius: 7,
        fill: "salmon",
        stroke: "black",
        strokeWidth: 1
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
      configAreas: [],
      configTextAreas: [],
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
      },
      warehouse: []
      // image: null
    };
  },

  created() {
    this.id = console.log(this.$route.params.id);
  },
  mounted() {
    this.getWarehouseDetail(1);
    this.sockets.subscribe("message", data => {
      // magicConstantX = 106.8565664;
      // magicConstantY = -6.3038096;
      this.configCirclePusat.y = (Number(data.lat) - -6.3038096) * 2500000 + 75;
      this.configCirclePusat.x =
        (Number(data.long) - 106.8565664) * 2500000 + 255;
      console.log({
        x: this.configCirclePusat.x,
        y: this.configCirclePusat.y
      });
    });
  },
  methods: {
    async getWarehouseDetail(id) {
      try {
        const response = await fetch(
          "https://ewms-ruby.herokuapp.com/warehouses/1"
        );
        const data = await response.json();
        // console.log(data);

        this.configOuter.height = Number(data.height);
        this.configOuter.width = Number(data.width);
        data.areas.forEach(area => {
          area.fill = this.colorsArea[area.jenis_vehicle_id - 1];
          area.x = Number(area.x);
          area.y = Number(area.y);
          area.width = Number(area.width);
          area.height = Number(area.height);
          var textArea = area;
          textArea.text = "Area " + area.id;
          textArea.fontSize = 36;
          this.configAreas.push(area);
          this.configTextAreas.push(textArea);
        });
        data.vehicles.forEach(vehicle => {
          var circle = vehicle;
          circle.y = (Number(vehicle.latitude) - -6.3038096) * 2500000 + 75;
          circle.x = (Number(vehicle.longitude) - 106.8565664) * 2500000 + 255;
          circle.fill = "salmon";
          circle.stroke = "black";
          circle.strokeWidth = 1;
          circle.radius = 7;
          this.configCircles.push(circle);
          console.log(circle);
        });
      } catch (error) {
        console.error(error);
      }
    }
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

<style></style>
