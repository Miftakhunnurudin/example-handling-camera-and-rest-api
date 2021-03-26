<template>
  <div class="home container d-flex">
    <div>
      <Camera/>
      <Map/>
    </div>
    <div class="content shadow-lg card p-1">
      <h3 class="mt-3 mb-3">Test Job Opportunity at PT. Gradana Teknoruci Indonesia</h3>
      <div class="row p-2">
        <Form class="col" :print_data="print_data"/>
        <div class="col">
          <div class="card shadow-sm ml-2 p-2" v-if="province">
            <table style="text-align:left">
              <tr>
                <td><h6>Province</h6></td>
                <td>:</td>
                <td>{{province}}</td>
              </tr>
              <tr>
                <td><h6>District</h6></td>
                <td>:</td>
                <td>{{district}}</td>
              </tr>
              <tr>
                <td><h6>Sub-District</h6></td>
                <td>:</td>
                <td>{{subDistrict}}</td>
              </tr>
              <tr>
                <td><h6>Village</h6></td>
                <td>:</td>
                <td>{{village}}</td>
              </tr>
              <tr>
                <td><h6>Postal Code</h6></td>
                <td>:</td>
                <td>{{postalCode}}</td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Camera from '../components/Camera'
import Map from '../components/Map'
import Form from '../components/Form'

export default {
  name: 'Home',
  components: {
    Camera,
    Map,
    Form
  },
  data () {
    return {
      province: null,
      district: null,
      subDistrict: null,
      village: null,
      postalCode: null
    }
  },
  methods: {
    print_data: function ({ province, district, subDistrict, village, postalCode }) {
      this.province = province
      this.district = district
      this.subDistrict = subDistrict
      this.village = village
      this.postalCode = postalCode
    }
  }
}
</script>
<style>
  .content {
    width: 100%;
    /* background-color: black; */
    margin-left: 20px;
  }
</style>
