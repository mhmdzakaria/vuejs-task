<template>
  <!-- <ApiComponent /> -->
  <FilterComponent />
  <InvoiceComponent />
</template>
<script>
import FilterComponent from './components/FilterComponent'
import InvoiceComponent from './components/InvoiceComponent'
// import ApiComponent from './components/ApiComponent'

export default {
  name: 'App',
  components: {
    FilterComponent,
    InvoiceComponent,
    // ApiComponent
  }
}
</script>
<style>
</style>
