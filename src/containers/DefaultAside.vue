<template>
  <div>
    <div style="padding:5% 15% 5% 5%;">
      <h4>
        <u>General Information</u>
      </h4>
      <b-row>
        <b-col class="pt-1" align="left">
          <ul style="padding:0;list-style-type:none;line-height:200%">
            <li>Luas Wilayah</li>
            <li>Wilayah Terpakai</li>
            <li>Wilayah Tersedia</li>
          </ul>
        </b-col>
        <b-col class="pt-1" sm="4" align="right">
          <ul style="padding:0;list-style-type:none;line-height:200%">
            <li>{{ (warehouse.width * warehouse.height).toFixed(2) }}m²</li>
            <li>{{ parseFloat(warehouse.luas_occupied).toFixed(2) }}m²</li>
            <li>{{ parseFloat(warehouse.luas_sisa).toFixed(2) }}m²</li>
          </ul>
        </b-col>
      </b-row>
      <b-button type="button" variant="secondary" @click="myModal = true" class="mr-1">Lihat Detail</b-button>
      <b-modal title="General Information" v-model="myModal" @ok="myModal = false">
        <h5>Informasi Umum</h5>
        <b-row>
          <b-col class="pt-1" align="left">
            <ul style="padding:0;list-style-type:none;line-height:200%">
              <li>Luas Wilayah</li>
              <li>Wilayah Terpakai</li>
              <li>Wilayah Tersedia</li>
            </ul>
          </b-col>
          <b-col class="pt-1" sm="2" align="right">
            <ul style="padding:0;list-style-type:none;line-height:200%">
              <li>400</li>
              <li>150</li>
              <li>250</li>
            </ul>
          </b-col>
        </b-row>
        <h5>Vehicle Tersedia</h5>
        <b-row>
          <b-col sm="6">
            <b-card>
              <blockquote class="card-blockquote">
                <h5 style="margin-bottom:0;" align="center">
                  <u>Excavator</u>
                </h5>
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
    </div>
    <div style="padding:5%;background-color:whitesmoke;overflow-y:scroll;height:405px;">
      <h4>
        <u>Daftar Area</u>
      </h4>
      <b-card
        class
        v-for="area in configAreas"
        v-bind:key="area.id"
        v-bind:style="{ backgroundColor: area.fill }"
      >
        <blockquote class="card-blockquote">
          <h5 align="left" style="margin-bottom:0;">Area {{ area.id }}</h5>
          <p align="left">{{ area.jenis_vehicle.nama_jenis_vehicle }}</p>
          <b-row>
            <b-col class="pt-1" align="left">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li>Luas</li>
                <li>Kapasitas</li>
                <li>Terisi</li>
                <li>Sisa Kapasitas</li>
              </ul>
            </b-col>
            <b-col class="pt-1" sm="6" align="right">
              <ul style="padding:0;list-style-type:none;line-height:200%">
                <li>{{ area.width * area.height }}m²</li>
                <li>{{ area.kapasitas }}</li>
                <li>{{ area.terisi }}</li>
                <li>{{ area.sisa_kapasitas }}</li>
              </ul>
            </b-col>
          </b-row>
        </blockquote>
      </b-card>
    </div>
  </div>
  <!-- <b-tabs>
    <b-tab>
      <template slot="title">
        <i class='icon-list'></i>
      </template>
      <b-list-group class="list-group-accent">
        <b-list-group-item class="list-group-item-accent-secondary bg-light text-center font-weight-bold text-muted text-uppercase small">
          Today
        </b-list-group-item>
        <b-list-group-item href="#" class="list-group-item-accent-warning list-group-item-divider">
          <div class="avatar float-right">
            <img class="img-avatar" src="img/avatars/7.jpg" alt="admin@bootstrapmaster.com">
          </div>
          <div>Meeting with
            <strong>Lucas</strong>
          </div>
          <small class="text-muted mr-3">
            <i class="icon-calendar"></i>&nbsp;&nbsp;1 - 3pm
          </small>
          <small class="text-muted">
            <i class="icon-location-pin"></i>&nbsp;&nbsp;Palo Alto, CA
          </small>
        </b-list-group-item>
        <b-list-group-item href="#" class="list-group-item-accent-info">
          <div class="avatar float-right">
            <img class="img-avatar" src="img/avatars/4.jpg" alt="admin@bootstrapmaster.com">
          </div>
          <div>Skype with <strong>Megan</strong>
          </div>
          <small class="text-muted mr-3"><i class="icon-calendar"></i>&nbsp;&nbsp;4 - 5pm</small>
          <small class="text-muted"><i class="icon-social-skype"></i>&nbsp;&nbsp;On-line</small>
        </b-list-group-item>
        <hr class="transparent mx-3 my-0">
        <b-list-group-item class="list-group-item-accent-secondary bg-light text-center font-weight-bold text-muted text-uppercase small">
          Tomorrow
        </b-list-group-item>
        <b-list-group-item href="#" class="list-group-item-accent-danger list-group-item-divider">
          <div>New UI Project - <strong>deadline</strong>
          </div>
          <small class="text-muted mr-3"><i class="icon-calendar"></i>&nbsp;&nbsp;10 - 11pm</small>
          <small class="text-muted"><i class="icon-home"></i>&nbsp;&nbsp;creativeLabs HQ</small>
          <div class="avatars-stack mt-2">
            <div class="avatar avatar-xs">
              <img class="img-avatar" src="img/avatars/2.jpg" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img class="img-avatar" src="img/avatars/3.jpg" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img class="img-avatar" src="img/avatars/4.jpg" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img class="img-avatar" src="img/avatars/5.jpg" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img class="img-avatar" src="img/avatars/6.jpg" alt="admin@bootstrapmaster.com">
            </div>
          </div>
        </b-list-group-item>
        <b-list-group-item href="#" class="list-group-item-accent-success list-group-item-divider">
          <div><strong>#10 Startups.Garden</strong> Meetup</div>
          <small class="text-muted mr-3"><i class="icon-calendar"></i>&nbsp; 1 - 3pm</small>
          <small class="text-muted"><i class="icon-location-pin"></i>&nbsp; Palo Alto, CA</small>
        </b-list-group-item>
        <b-list-group-item href="#" class="list-group-item-accent-primary list-group-item-divider">
          <div><strong>Team meeting</strong></div>
          <small class="text-muted mr-3"><i class="icon-calendar"></i>&nbsp; 4 - 6pm</small>
          <small class="text-muted"><i class="icon-home"></i>&nbsp; creativeLabs HQ</small>
          <div class="avatars-stack mt-2">
            <div class="avatar avatar-xs">
              <img src="img/avatars/2.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img src="img/avatars/3.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img src="img/avatars/4.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img src="img/avatars/5.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img src="img/avatars/6.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img src="img/avatars/7.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
            </div>
            <div class="avatar avatar-xs">
              <img src="img/avatars/8.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
            </div>
          </div>
        </b-list-group-item>
      </b-list-group>
    </b-tab>
    <b-tab>
      <template slot="title">
        <i class='icon-speech'></i>
      </template>
      <div class="p-3">
        <div class="message">
          <div class="py-3 pb-5 mr-3 float-left">
            <div class="avatar">
              <img src="img/avatars/7.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
              <b-badge variant="success" class="avatar-status"></b-badge>
            </div>
          </div>
          <div>
            <small class="text-muted">Lukasz Holeczek</small>
            <small class="text-muted float-right mt-1">1:52 PM</small>
          </div>
          <div class="text-truncate font-weight-bold">Lorem ipsum dolor sit amet</div>
          <small class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt...</small>
        </div>
        <hr>
        <div class="message">
          <div class="py-3 pb-5 mr-3 float-left">
            <div class="avatar">
              <img src="img/avatars/7.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
              <b-badge variant="danger" class="avatar-status"></b-badge>
            </div>
          </div>
          <div>
            <small class="text-muted">Lukasz Holeczek</small>
            <small class="text-muted float-right mt-1">1:52 PM</small>
          </div>
          <div class="text-truncate font-weight-bold">Lorem ipsum dolor sit amet</div>
          <small class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt...</small>
        </div>
        <hr>
        <div class="message">
          <div class="py-3 pb-5 mr-3 float-left">
            <div class="avatar">
              <img src="img/avatars/7.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
              <b-badge variant="info" class="avatar-status"></b-badge>
            </div>
          </div>
          <div>
            <small class="text-muted">Lukasz Holeczek</small>
            <small class="text-muted float-right mt-1">1:52 PM</small>
          </div>
          <div class="text-truncate font-weight-bold">Lorem ipsum dolor sit amet</div>
          <small class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt...</small>
        </div>
        <hr>
        <div class="message">
          <div class="py-3 pb-5 mr-3 float-left">
            <div class="avatar">
              <img src="img/avatars/7.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
              <b-badge variant="warning" class="avatar-status"></b-badge>
            </div>
          </div>
          <div>
            <small class="text-muted">Lukasz Holeczek</small>
            <small class="text-muted float-right mt-1">1:52 PM</small>
          </div>
          <div class="text-truncate font-weight-bold">Lorem ipsum dolor sit amet</div>
          <small class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt...</small>
        </div>
        <hr>
        <div class="message">
          <div class="py-3 pb-5 mr-3 float-left">
            <div class="avatar">
              <img src="img/avatars/7.jpg" class="img-avatar" alt="admin@bootstrapmaster.com">
              <b-badge variant="dark" class="avatar-status"></b-badge>
            </div>
          </div>
          <div>
            <small class="text-muted">Lukasz Holeczek</small>
            <small class="text-muted float-right mt-1">1:52 PM</small>
          </div>
          <div class="text-truncate font-weight-bold">Lorem ipsum dolor sit amet</div>
          <small class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt...</small>
        </div>
      </div>
    </b-tab>
    <b-tab>
      <template slot="title">
        <i class='icon-settings'></i>
      </template>
      <div class="p-3">
        <h6>Settings</h6>
        <div class="aside-options">
          <div class="clearfix mt-4">
            <small><b>Option 1</b></small>
            <c-switch color="success" label variant="pill" size="sm" class="float-right" checked />
          </div>
          <div>
            <small class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</small>
          </div>
        </div>
        <div class="aside-options">
          <div class="clearfix mt-3">
            <small><b>Option 2</b></small>
            <c-switch color="success" label variant="pill" size="sm" class="float-right" />
          </div>
          <div>
            <small class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</small>
          </div>
        </div>
        <div class="aside-options">
          <div class="clearfix mt-3">
            <small><b>Option 3</b></small>
            <c-switch color="success" label variant="pill" size="sm" class="float-right" disabled defaultChecked/>
          </div>
          <div>
            <small class="text-muted">Disabled option.</small>
          </div>
        </div>
        <div class="aside-options">
          <div class="clearfix mt-3">
            <small><b>Option 4</b></small>
            <c-switch color="success" label variant="pill" size="sm" class="float-right" checked />
          </div>
        </div>
        <hr>
        <h6>System Utilization</h6>
        <div class="text-uppercase mb-1 mt-4">
          <small><b>CPU Usage</b></small>
        </div>
        <b-progress height={} class="progress-xs" variant="info" :value="25"></b-progress>
        <small class="text-muted">348 Processes. 1/4 Cores.</small>
        <div class="text-uppercase mb-1 mt-2">
          <small><b>Memory Usage</b></small>
        </div>
        <b-progress height={} class="progress-xs" variant="warning" :value="70"></b-progress>
        <small class="text-muted">11444GB/16384MB</small>
        <div class="text-uppercase mb-1 mt-2">
          <small><b>SSD 1 Usage</b></small>
        </div>
        <b-progress height={} class="progress-xs" variant="danger" :value="95"></b-progress>
        <small class="text-muted">243GB/256GB</small>
        <div class="text-uppercase mb-1 mt-2">
          <small><b>SSD 2 Usage</b></small>
        </div>
        <b-progress height={} class="progress-xs" variant="success" :value="10"></b-progress>
        <small class="text-muted">25GB/256GB</small>
      </div>
    </b-tab>
  </b-tabs>-->
</template>

<script>
// import { Switch as cSwitch } from '@coreui/vue'
export default {
  name: "DefaultAside",
  // components: {
  //   cSwitch
  // }
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
      myModal: false,
      warehouse: [],
      configAreas: []
    };
  },

  mounted() {
    this.getWarehouseDetail(1);
  },

  methods: {
    async getWarehouseDetail(id) {
      try {
        const response = await fetch(
          "https://ewms-ruby.herokuapp.com/warehouses/1"
        );
        const data = await response.json();
        this.warehouse = data;
        console.log(data);

        // this.configOuter.height = Number(data.height);
        // this.configOuter.width = Number(data.width);
        data.areas.forEach(area => {
          // area.fill = this.colorsArea[area.jenis_vehicle_id - 1];
          area.x = Number(area.x);
          area.y = Number(area.y);
          area.width = Number(area.width);
          area.height = Number(area.height);
          this.configAreas.push(area);
        });
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>
