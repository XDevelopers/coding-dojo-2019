<template>
  <div class="home">
    <img class="logo" alt="Vue logo" src="../assets/logo.png" >
    <DataTable msg=""/>

  </div>
</template>

<script>
// @ is an alias to /src
import DataTable from '@/components/DataTable.vue'

export default {
  name: 'home',
  components: {
    DataTable
  }
}
</script>


<style scopep>
.home {
  text-align: center;
}
.logo {
  width: 5.85rem;
}
</style>

