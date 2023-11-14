<template>
  <v-app id="inspire" >
    <v-navigation-drawer v-model="drawer" class="bg-red">
      <v-list-item title="My Application" subtitle="AAD Informatica Frontend"></v-list-item>
      <v-divider></v-divider>
      <v-list-item link title="List Item 1"></v-list-item>
      <v-list-item link title="List Item 2"></v-list-item>
      <v-list-item link title="List Item 3"></v-list-item>          
    </v-navigation-drawer>

    <v-app-bar class="bg-red-lighten-1">
      <v-app-bar-nav-icon @click="drawer = !drawer">
        <v-icon icon="mdi-menu" size="large"></v-icon>
      </v-app-bar-nav-icon>

      <v-app-bar-title>Applicatie naam</v-app-bar-title>
    </v-app-bar>

    <v-main class="bg-red-lighten-5">

      <!-- Maak een container (grid) aan voor onze content  -->
      <v-container>
        <v-col> <!--  Onze container heeft één column-->
          <v-row>
            <h1>Voorbeeldrij 1</h1>
            <ProductSalesChart></ProductSalesChart>
          </v-row>
          <v-row>
            <h1>Voorbeeldrij 2</h1>
            <PopulationChart></PopulationChart>
          </v-row>
          <v-row>
            <h1>Voorbeeldrij 3</h1>
          </v-row>
        </v-col>

      </v-container>    
    </v-main>
  </v-app>
</template>

<script>

  import { ref } from 'vue'
  import ProductSalesChart from '@/components/ProductSalesChart.vue'
  import PopulationChart from './components/PopulationChart.vue'

  const drawer = ref(null)

  export default {
    name: 'App',
    components: {
      ProductSalesChart,
      PopulationChart
    },
    data() {
      return {
        drawer: null
      }
    } 

  }
</script>

<style>


</style>
