<template>
  <div class="animated fadeIn">
    <br/>  
    <b-button size="lg" variant="primary" @click="submitModal = true" class="btn-pill">
      <i class="fa fa-plus"></i>&nbsp;&nbsp;Submit New Project
    </b-button>
    <b-modal title="Submit New Project" v-model="submitModal" @ok="submitModal = false">
      <b-form>
      <b-form-group
      description=""
      label="Nama"
      label-for="basicName"
      :label-cols="3"
      >
      <b-form-input id="basicName" type="text" autocomplete="name"></b-form-input>
      </b-form-group>
      <b-form-group
      description=""
      label="Lokasi"
      label-for="basicText"
      :label-cols="3"
      >
      <b-form-input id="basicText" type="text" placeholder="Text"></b-form-input>
      </b-form-group>
      <b-form-group
      label="Tanggal Mulai" label-for="date"
      :label-cols="3"
      >
      <b-form-input type="date" id="date"></b-form-input>
      </b-form-group>
      <b-form-group
      label="Tanggal Selesai" label-for="date"
      :label-cols="3"
      >
      <b-form-input type="date" id="date"></b-form-input>
      </b-form-group>
      <b-form-group
      label="Vehicle"
      label-for="basicSelect"
      :label-cols="3"
      >
      <b-form-select id="basicSelect"
          :plain="true"
          :options="['Please select','Option 1', 'Option 2', 'Option 3']"
          value="Please select">
      </b-form-select>
      <b-form-input id="basicText" type="text" placeholder="Text"></b-form-input>
      </b-form-group>
      <b-button type="submit" size="sm" variant="primary"><i class="fa fa-dot-circle-o"></i> Submit</b-button>
      <b-button type="reset" size="sm" variant="danger"><i class="fa fa-ban"></i> Reset</b-button>
      </b-form>
    </b-modal>
    <b-row>
      <b-col>
        <h3 style="padding:5% 0 2%;">Ketersediaan</h3>
        <b-col align="center" align-h="center" v-for="warehouse in warehouses" :key="warehouse.id">
            <b-card
            header-bg-variant=""
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
      </b-col>
      <b-col>
        <h3 style="padding:5% 0 2%;">Unplotted Projects</h3>
        <b-card header="Project A" header-bg-variant="">
          <b-row>
            <b-col align="left" sm="4">
              <p>Lokasi</p>
            </b-col>
            <b-col align="left">
              <p>Somewhere over the rainbow</p>
            </b-col>
          </b-row>
          <b-row>
            <b-col align="left" sm="4">
              <p>Tgl Mulai</p>
            </b-col>
            <b-col align="left">
              <p>11 November 2019</p>
            </b-col>
          </b-row>
          <b-row>
            <b-col align="left" sm="4">
              <p>Tgl Selesai</p>
            </b-col>
            <b-col align="left">
              <p>10 Oktober 2020</p>
            </b-col>
          </b-row>
          <b-button type="button" variant="secondary" @click="myModal = true" class="mr-1">Lihat Detail</b-button>
          <b-modal title="Project A" v-model="myModal" @ok="myModal = false">
              <h5>Informasi Umum</h5>
              <b-row>
              <b-col class="pt-1" sm="4" align="left">
                  <ul style="padding:0;list-style-type:none;line-height:200%">
                  <li>Lokasi</li>
                  <li>Waktu Mulai</li>
                  <li>Waktu Selesai</li>
                  </ul>
              </b-col>
              <b-col class="pt-1" align="left">
                  <ul style="padding:0;list-style-type:none;line-height:200%">
                  <li>Somewhere over the rainbow</li>
                  <li>11 November 2019</li>
                  <li>10 Oktober 2020</li>
                  </ul>
              </b-col>
              </b-row>
              <h5>Kebutuhan</h5>
              <b-row>
              <b-col sm="6">
                  <b-card>
                  <blockquote class="card-blockquote">
                      <h5 style="margin-bottom:0;" align="center"><u>Excavator</u></h5>
                      <b-row>
                      <b-col class="pt-1" align="left">
                          <ul style="padding:0;list-style-type:none;line-height:200%">
                          <li>Unit</li>
                          <li>Rata2 Transit</li>
                          </ul>
                      </b-col>
                      <b-col class="pt-1" sm="5" align="right">
                          <ul style="padding:0;list-style-type:none;line-height:200%">
                          <li>500 unit</li>
                          <li>14 hari</li>
                          </ul>
                      </b-col>
                      </b-row>
                  </blockquote>
                  </b-card>
              </b-col>
              </b-row>
          </b-modal>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "DashboardM",
  data() {
    return {
      warehouses: [],
      myModal: false,
      submitModal: false
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