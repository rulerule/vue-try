<template>
  <div class="container">
    <app-header></app-header>
    <hr>
    <div class="row">
      <servers></servers>
      <app-server-details></app-server-details>
    </div>
    <hr>
    <app-footer></app-footer>
  </div>
</template>

<script>
import Header from './header.vue'
import Footer from './footer.vue'
import Servers from './servers.vue'
import ServerDetails from './serverDetails.vue'

export default {
  components: {
    appHeader: Header,
    Servers,
    'app-server-details': ServerDetails,
    'app-footer': Footer
  }
}
</script>

<style>

</style>
