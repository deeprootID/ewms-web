<template>
  <div class="animated fadeIn">
    <br />
    <b-row align="center" align-h="center">
      <b-col v-for="warehouse in warehouses" sm="5" :key="warehouse.id">
        <b-card
          header-bg-variant="primary"
          @click="sendDashboard(warehouse.id)"
        >
          <div slot="header">
            <big>{{warehouse.nama_warehouse}}</big><br/>
            <small>{{warehouse.alamat}}</small>
          </div>
          <b-row>
            <b-col>
              <p>Luas: {{warehouse.width * warehouse.height}} m²</p>
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
                <li v-for="(value, key, count) in warehouse.jumlah_jenis_vehicle">
                  <span v-if="count%2==0">{{ key }}</span>
                </li>
              </ul>
            </b-col>
            <b-col style="border-right:0.5pt solid lightgrey;" class="pt-1" sm="2" align="right">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li v-for="(value, key, count) in warehouse.jumlah_jenis_vehicle">
                  <span v-if="count%2==0">{{ value }}</span>
                </li>
              </ul>
            </b-col>
            <b-col class="pt-1" align="left">
              <ul style="padding:0;list-style-type:none;line-height:200%" class="pt-1">
                <li v-for="(value, key, count) in warehouse.jumlah_jenis_vehicle">
                  <span v-if="count%2==1">{{ key }}</span>
                </li>
              </ul>
            </b-col>
            <b-col class="pt-1" sm="2" align="right">
              <ul style="padding:0;list-style-type:none;line-height:200%" class="pt-1">
                <li v-for="(value, key, count) in warehouse.jumlah_jenis_vehicle">
                  <span v-if="count%2==1">{{ value }}</span>
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
  name: "warehouse",
  data() {
    return {
      warehouses: []
    };
  },
  mounted() {
    this.getWarehouses();
  },
  methods: {
    async getWarehouses() {
      try {
        const response = await fetch(
          "https://ewms-ruby.herokuapp.com/warehouses/get_jumlah_jenis_vehicle"
        );
        const data = await response.json();
        this.warehouses = data;
        console.log(data);
      } catch (error) {
        console.error(error);
      }
    },
    sendDashboard(id) {
      this.$router.push({ name: "Dashboard_id", params: { id: id } });
    }
  }
};
</script>