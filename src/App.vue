<template>
  <router-view></router-view>
</template>

<script>
export default {
  name: 'app',

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

<style lang="scss">
  // CoreUI Icons Set
  @import '~@coreui/icons/css/coreui-icons.min.css';
  /* Import Font Awesome Icons Set */
  $fa-font-path: '~font-awesome/fonts/';
  @import '~font-awesome/scss/font-awesome.scss';
  /* Import Simple Line Icons Set */
  $simple-line-font-path: '~simple-line-icons/fonts/';
  @import '~simple-line-icons/scss/simple-line-icons.scss';
  /* Import Flag Icons Set */
  @import '~flag-icon-css/css/flag-icon.min.css';
  /* Import Bootstrap Vue Styles */
  @import '~bootstrap-vue/dist/bootstrap-vue.css';
  // Import Main styles for this application
  @import 'assets/scss/style';
</style>
