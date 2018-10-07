<template lang="pug">
section.offices
  .offices__contener
    .offices__wrapper
        .offices__header
            h2.offices__title Our Offices
        .offices__tabs
            ul.offices__tabs-list
                li(v-for="tab in tabs" :class="{'is-active': tab.active}" class="offices__tabs-item")
                    a(@click="setActive(tab)" href="javascript:void(0);" ) {{tab.city}}
            .offices__tab
                .offices__tab-title {{currentTab.title}}
                .offices__addres {{currentTab.street}}
                .offices__zip {{currentTab.zip}}
                .offices__country {{currentTab.country}}

    .map__wrapper
        GoogleMap(name="name", :coordinates='currentTab.coordinates')
</template>

<script>
import GoogleMap from './GoogleMap.vue'
export default {
  name: 'offices',
  data () {
    return {
      tabs: [
        {
          city: 'Kyiv',
          title: 'Global Message Services Ukraine LLC',
          street: 'Kuiv, Stepan Bandera, 33',
          zip: '02066',
          country: 'Ukraine',
          coordinates: {
            x: 50.4481233,
            y: 30.5039585
          },
          active: true
        },
        {
          city: 'New York',
          title: 'Global Message Services USA LLC',
          street: 'New York, Stepan Bandera, 33',
          zip: '02066',
          country: 'USA',
          coordinates: {
            x: 40.6721704,
            y: -73.9505706
          },
          active: false
        },
        {
          city: 'Guangzhou',
          title: 'Global Message Services USA LLC',
          street: 'Guangzhou, Stepan Bandera, 33',
          zip: '02066',
          country: 'USA',
          coordinates: {
            x: 22.9523694,
            y: 113.4292872
          },
          active: false
        },
        {
          city: 'Barcelona',
          title: 'Global Message Services USA LLC',
          street: 'Barcelona, Stepan Bandera, 33',
          zip: '02066',
          country: 'USA',
          coordinates: {
            x: 41.3908745,
            y: 2.186112
          },
          active: false
        }
      ]
    }
  },
  methods: {
    setActive (tab) {
      this.tabs.forEach(el => {
        el.active = el === tab
      })
    }
  },
  computed: {
    currentTab () {
      return this.tabs.reduce((accum, curr) => { return curr.active ? curr : accum }, {})
    }
  },
  components: {
    GoogleMap
  }
}
</script>
