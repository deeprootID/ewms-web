<template>
  <div class="animated fadeIn">
    <br />
    <h3 align="center" style="padding:1%;">Unplotted Projects</h3>
    <b-row align="center" align-h="center">
      <b-col sm="6" md="4">
        <b-card header="Project A" header-bg-variant="secondary">
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
          <b-button type="button" variant="secondary" @click="myModal1 = true" class="mr-1">Lihat Detail</b-button>
          <b-modal title="Project A" v-model="myModal1" @ok="myModal1 = false">
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
    <br />
    <h3 align="center" style="padding-bottom:1%;">Plotted Projects</h3>
    <b-row align="center" align-h="center">
      <b-col sm="6" md="4">
        <b-card header="Project B" header-bg-variant="primary">
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
          <b-button type="button" variant="secondary" @click="myModal2 = true" class="mr-1">Lihat Detail</b-button>
          <b-modal title="Project B" v-model="myModal2" @ok="myModal2 = false">
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
    <br />
    <h3 align="center" style="padding-bottom:1%;">Running Projects</h3>
    <b-row align="center" align-h="center">
      <b-col sm="6" md="4">
        <b-card header="Project C" header-bg-variant="success">
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
          <b-button type="button" variant="secondary" @click="myModal3 = true" class="mr-1">Lihat Detail</b-button>
          <b-modal title="Project C" v-model="myModal3" @ok="myModal3 = false">
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
  name: 'Projects',
  data () {
    return {
      myModal1: false,
      myModal2: false,
      myModal3: false
    }
  }
}
</script>