<template>
  <div id="app">
    <nav-tabs></nav-tabs>
      <router-view></router-view>
  </div>
</template>

<script>
import NavTabs from './components/Nav-tabs.vue'

export default {
  name: 'App',
  components:{
    NavTabs
  }
}
</script>

