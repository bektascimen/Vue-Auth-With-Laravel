<template>
  <div id="app">
    <TheNavigation />
    <router-view/>
  </div>
</template>

<script>
import Vue from 'vue'
import TheNavigation from '@/components/TheNavigation'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.use(BootstrapVue)
Vue.use(IconsPlugin)

export default {
  components: {
    TheNavigation
  }
}
</script>