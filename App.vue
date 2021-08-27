<template>
  <personaldiary/>
  <diary/>
  <datepicker v-model="date" lang="en" type="date" format="yyyy-mm-dd"></datepicker>
    <sidebar/>

</template>

<script>
import personaldiary from './components/personaldiary.vue'
import sidebar from './components/sidebar.vue'
import datepicker from './components/datepicker.vue'
import diary from './components/diary.vue'
export default {
  name: 'App',
  components: {
    personaldiary,
    sidebar,
    datepicker,
    diary
  }
  }

</script>

<style>

</style>
