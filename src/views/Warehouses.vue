<template>
  <div class="animated fadeIn">
    <br>
    <b-row align="center" align-h="center">
      <b-col v-for="warehouse in warehouses" sm="6" md="4" :key="warehouse.id">
        <b-card :header=warehouse.nama_warehouse header-bg-variant="primary" :sub-title=warehouse.alamat>
          <b-row>
            <b-col>
              <p>Luas Terpakai</p>
            </b-col>
            <b-col>
              <p>{{warehouse.luas}} m²</p>
            </b-col>
          </b-row>
          <b-row>
              <b-col>
                  <ul style="list-style-type:none;">
                    <li v-for="(value, key, count) in warehouse.jumlah_jenis_vehicle">
                      <span v-if="count%2==0">{{ key }} : {{value}}</span>
                    </li>
                  </ul>
              </b-col>
              <b-col>
                  <ul style="list-style-type:none;">
                    <li v-for="(value, key, count) in warehouse.jumlah_jenis_vehicle">
                      <span v-if="count%2==1">{{ key }} : {{value}}</span>
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
  name: 'warehouse',
  data() {
    return {
      warehouses: []
    }
  },
  mounted() {
    this.getWarehouses()
  },
  methods: {
    async getWarehouses() {
      try {
        const response = await fetch('http://localhost:3000/warehouses/get_jumlah_jenis_vehicle')
        const data = await response.json()
        this.warehouses = data
        console.log(data)
      } catch (error) {
        console.error(error)
      }
    }
  }
}
</script>