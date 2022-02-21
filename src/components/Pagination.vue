<template>
  <div class="pt-3">
    <div class="justify-center">
      <input class="w-4/5 sm:3/4 md:w-2/3 lg:w-1/2 text-lg py-4 ring border-2 focus:ring-teal-500 focus:border-teal-500 border-teal-300 px-7 rounded-md" v-model="recipeName" placeholder="Search titles, ingredients or categories"/>
    </div>
    <!-- Sends recipeName string to the database through DataLoader to query for the total amount of items returned -->
    <DataLoader
      :endpoint="`${web}?recipe_name=${recipeName}`"
      :authToken="authToken"
    >
      <template #loaded="{data}">
        <!-- Once the database information from the DataLoader template slot has been loaded, in theory, its total amount is sent as a prop to VSPagination -->
        <VSPagination :totalItems="data.count">
          <!-- From the data slot in VSPagination, the following props are obtained -->
          <template #data="{pageNumber, itemsPerPage}">
            <!-- The aforementioned props above are used to query the DataLoader :endpoint and obtain the data once again -->
            <DataLoader
              :endpoint="`${web}?page=${pageNumber}&size=${itemsPerPage}&recipe_name=${recipeName}`"
              :authToken="authToken"
            > 
              <!-- The loading-messages template would be temporarily active, before an error timeout or data being loaded -->
              <template #loading-message>
                <h3>Loading your recipes</h3>
              </template>
              <template #error>
                We could not find recipes containing
                <strong>{{ recipeName }}</strong>
              </template>
              <!-- Data requested from the database will be sent as a prop to VSCards as :items="data.results -->
              <template #loaded="{data}">
                <VSCards :items="data.results || []">
                </VSCards>
              </template>
            </DataLoader>
          </template>
        </VSPagination>
      </template>
    </DataLoader>
  </div>
</template>

<script>
import VSCards from "@/components/VSCards.vue";
import DataLoader from "@/components/DataLoader.vue";
import VSPagination from "@/components/VSPagination.vue";

export default {
  components: {
    DataLoader,
    VSPagination,
    VSCards,
  },
  data() {
    return {
      recipeName: this.$route.query.recipeName || "",
      authToken: "", // authToken is pending future usage with Django auth
      web: process.env.VUE_APP_LOCAL_DB + "/filterrecipes"
      // web: "http://127.0.0.1:8000/filterrecipes"
    };
  },
  watch: {
    recipeName(newrecipeName) {
      this.$router.push({
        path: this.$route.path,
        query: {
          ...this.$route.query,
          recipe_name: newrecipeName,
          pageNumber: 1,
        },
      });
    },
  },
};
</script>
