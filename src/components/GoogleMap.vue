<template lang="pug">
    .google-map(:id="name")
</template>
<script>
import {googleMapStyle} from '../config'
import marcerImg from '../assets/images/marcer.png'

export default {
  name: 'google-map',
  props: ['name', 'coordinates'],
  data: function () {
    return {
      map: '',
      marker: ''
    }
  },
  mounted: function () {
    const element = document.getElementById(this.name)
    // eslint-disable-next-line
    const myLatlng = new google.maps.LatLng(this.coordinates.x, this.coordinates.y);
    // eslint-disable-next-line
    this.marker = new google.maps.Marker({
      position: myLatlng,
      icon: marcerImg
    })
    const options = {
      zoom: 14,
      center: myLatlng,
      styles: googleMapStyle,
      disableDefaultUI: true
    }
    // eslint-disable-next-line
    this.map = new google.maps.Map(element, options)
    this.marker.setMap(this.map)
  },
  watch: {
    coordinates (newQuestion) {
      this.marker.setMap(null)
      // eslint-disable-next-line
      const newLatlng = new google.maps.LatLng(newQuestion.x, newQuestion.y)
      // eslint-disable-next-line
      this.marker = new google.maps.Marker({
        position: newLatlng,
        icon: marcerImg
      })
      this.map.setCenter(newLatlng)
      this.marker.setMap(this.map)
    }
  },
  methods: {
  }
}
</script>
<style scoped>
.google-map {
    width:100%;
    height: 500px;
    margin: 0 auto;
    background: gray;
}
</style>
