<template>
  <div class="animated fadeIn">
    <br />
    <b-row align="center" align-h="center">
      <b-col v-for="vehicle in vehicles" sm="6" :key="vehicle.id">
        <b-card header-bg-variant="primary">
          <div slot="header">
            <big>{{ vehicle.nama_jenis_vehicle }}</big>
          </div>
          <b-row>
            <b-col>
              <p style="margin-bottom:0;">
                Sedang digunakan:
              </p>
              <p>
                <strong>
                  {{
                    vehicle.jumlah_seluruh_kendaraan_sedang_dipakai_tiap_warehouse
                  }}
                  unit
                </strong>
              </p>
            </b-col>
          </b-row>
          <b-row style="border-bottom:0.5pt solid lightgrey;">
            <b-col>
              <h5>Tersedia</h5>
            </b-col>
          </b-row>
          <b-row>
            <b-col class="pt-1" align="left">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li
                  v-for="(value,
                  key,
                  count) in vehicle.jumlah_seluruh_kendaraan_tersedia_tiap_warehouse"
                >
                  <span v-if="count % 2 == 0">{{ key }}</span>
                </li>
              </ul>
            </b-col>
            <b-col
              style="border-right:0.5pt solid lightgrey;"
              class="pt-1"
              sm="2"
              align="right"
            >
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li
                  v-for="(value,
                  key,
                  count) in vehicle.jumlah_seluruh_kendaraan_tersedia_tiap_warehouse"
                >
                  <span v-if="count % 2 == 0">{{ value }}</span>
                </li>
              </ul>
            </b-col>
            <b-col class="pt-1" align="left">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li
                  v-for="(value,
                  key,
                  count) in vehicle.jumlah_seluruh_kendaraan_tersedia_tiap_warehouse"
                >
                  <span v-if="count % 2 == 1">{{ key }}</span>
                </li>
              </ul>
            </b-col>
            <b-col class="pt-1" sm="2" align="right">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li
                  v-for="(value,
                  key,
                  count) in vehicle.jumlah_seluruh_kendaraan_tersedia_tiap_warehouse"
                >
                  <span v-if="count % 2 == 1">{{ value }}</span>
                </li>
              </ul>
            </b-col>
          </b-row>
          <b-row style="border-bottom:0.5pt solid lightgrey;">
            <b-col>
              <h5>Under Maintenance</h5>
            </b-col>
          </b-row>
          <b-row>
            <b-col class="pt-1" align="left">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li
                  v-for="(value,
                  key,
                  count) in vehicle.jumlah_seluruh_kendaraan_under_maintenance_tiap_warehouse"
                >
                  <span v-if="count % 2 == 0">{{ key }}</span>
                </li>
              </ul>
            </b-col>
            <b-col
              style="border-right:0.5pt solid lightgrey;"
              class="pt-1"
              sm="2"
              align="right"
            >
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li
                  v-for="(value,
                  key,
                  count) in vehicle.jumlah_seluruh_kendaraan_under_maintenance_tiap_warehouse"
                >
                  <span v-if="count % 2 == 0">{{ value }}</span>
                </li>
              </ul>
            </b-col>
            <b-col class="pt-1" align="left">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li
                  v-for="(value,
                  key,
                  count) in vehicle.jumlah_seluruh_kendaraan_under_maintenance_tiap_warehouse"
                >
                  <span v-if="count % 2 == 1">{{ key }}</span>
                </li>
              </ul>
            </b-col>
            <b-col class="pt-1" sm="2" align="right">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li
                  v-for="(value,
                  key,
                  count) in vehicle.jumlah_seluruh_kendaraan_under_maintenance_tiap_warehouse"
                >
                  <span v-if="count % 2 == 1">{{ value }}</span>
                </li>
              </ul>
            </b-col>
          </b-row>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "vehicles",
  data() {
    return {
      vehicles: []
    };
  },
  mounted() {
    this.getVehicles();
  },
  methods: {
    async getVehicles() {
      try {
        const response = await fetch(
          "https://ewms-ruby.herokuapp.com/jenis_vehicles/jumlah_seluruh_kendaraan_tersedia_tiap_warehouse"
        );
        const data = await response.json();
        data.forEach(vehicle => {
          var sum = 0;
          for (const [key, value] of Object.entries(
            vehicle.jumlah_seluruh_kendaraan_tersedia_tiap_warehouse
          )) {
            sum += value;
          }
          vehicle.total = sum;
          this.vehicles.push(vehicle);
        });
        console.log(data);
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>
