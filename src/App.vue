<template>
  <v-app>
    <v-main>
      <v-row class="text-center">
        <v-col cols="12">
          <v-img
            :src="require('@/assets/logo.svg')"
            class="my-3"
            contain
            height="80"
          />
        </v-col>
      </v-row>
      <DgtekGoogleAutocomplete />
    </v-main>
  </v-app>
</template>

<script>

import 'dgtek-styles'

export default {
  name: 'App',

  components: {
    DgtekGoogleAutocomplete: () => import('@/views/DgtekGoogleAutocomplete.vue')
  },

  methods: {
    showEvent (event) {
      console.log(event.detail)
    }
  },

  mounted () {
    window[Symbol.for('api.host')] = process.env.NODE_ENV === 'production' ? 'https://portal.dgtek.net' : 'https://dgtek-staging.herokuapp.com'
    window.addEventListener('new-address-data', this.showEvent)
  }
}
</script>

<style>
.theme--light.v-list-item .v-list-item__mask {
  color: #83332C !important;
  background: transparent !important;
}

* {
  outline: none!important;
  user-select: none!important;
}
</style>
