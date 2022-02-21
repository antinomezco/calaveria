<template>
  <div class="" v-if="loading">
    <slot name="loading">
      <Spinner />
    </slot>
  </div>
  <div v-else class="pt-3">
    <div class="flex justify-center">
      <div class="w-3/4">
        <div
          class="relative h-80 w-full object-cover rounded"
          :style="{ 'background-image': 'url(' + this.data.image + ')', 'background-position' : 'center', 'background-size' : 'cover' }"
          alt=""
        >
        <router-link to="/" class="absolute top-5 left-0 bg-clip-padding  rounded-r-lg shadow-lg bg-gray-200 pl-5 py-2 pr-2">
          <img src="../assets/chef.png" class="h-16" />
        </router-link>
        </div>
        <div class="">
          <div class="">
            <h1 class="text-4xl py-14 font-bold">
              {{ this.data.recipe_name }}
            </h1>
          </div>
          <div class="w-full border-t border-gray-400"></div>
          <div class="flex flex-row justify-between my-4" v-if="!loading">
            <div class="text-left">
              <div class="">
                <span class="">Category: </span
                >{{ this.data.food_category.food_category_name }}
              </div>
              <div class="">
                <span class="">Cuisine: </span
                >{{ this.data.cuisine.cuisine_name }}
              </div>
              <div class="">
                <span class="">Added by: </span>{{ this.data.first_name }}
              </div>
            </div>
            <div class="text-right">
              <div class="">
                <div>
                  <span class="">Prep time:</span> {{ this.data.prep_time }}
                </div>
                <div>
                  <span class="">Cook time:</span> {{ this.data.cook_time }}
                </div>
              </div>
              <div class="">
                <span class="">Meal: </span>{{ this.data.course.course_name }}
              </div>
            </div>
          </div>
          <div class="w-full border-t border-gray-400"></div>
          <div class="text-left pt-5">
            <div class="grid grid-cols-12 ">
              <!-- added v-if="!loading" to prevent v-for from trigerring an error 
            before there's any data to iterate -->
              <div class="col-span-12 lg:col-span-6" v-if="!loading">
                <div class="">
                  <div
                    class="block p-6 rounded-lg shadow-lg bg-yellow-50 "
                  >
                    <p class="text-yellow-600 font-bold text-2xl mb-2">
                      Ingredients for {{ data.servings }} servings
                    </p>
                    <p
                      v-for="(ing, index) in data.ingredients_text.split('\n')"
                      :key="index"
                      class="text-gray-700 text-xl text-base mb-1"
                    >
                      {{ ing }}
                    </p>
                  </div>
                </div>
              </div>
              <div class="col-span-12 lg:col-span-6" v-if="!loading">
                <div class=" ">
                  <div
                    class="block p-6"
                  >
                    <p class="text-red-600 font-bold text-2xl mb-2">Directions</p>
                    <div
                      v-for="(dir, index) in data.recipe_steps.split('\n')"
                  :key="index"
                      class="text-gray-700 text-xl text-base mb-1"
                    >
                      <div v-if="dir.trim()">{{ dir }}
                        <div class="w-full border-t border-gray-300"></div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="" v-if="!loading">
              <p class="text-red-600 font-bold text-2xl mb-2" v-if="data.recipe_notes.trim()">Notes</p>
              <p
                v-for="note in data.recipe_notes.split('\n')"
                :key="note"
                class="text-lg"
              >
                {{note}}
              </p>
            </div>
          </div>
        </div>
        <button @click="editPageGo" class="text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center m-5 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900">Edit Recipe</button>
      </div>
    </div>
  </div>
</template>

<script>
import Spinner from "@/components/Spinner.vue";
export default {
  components: {
    Spinner,
  },
  props: {
    slug: { required: true },
  },
  data() {
    return {
      // oneRecipe: "https://cookingdb.herokuapp.com/recipe/",
      oneRecipe: process.env.VUE_APP_LOCAL_DB + "/recipe/",
      data: [],
      loading: null,
      errorMessage: false,
    };
  },
  async created() {
    try {
      // Using :oneRecipe + this.slug (prop from Pagination.vue)
      // and tries to load results from the database through Axios
      this.error = null;
      this.loading = true; //while true, the loading slot will be active
      let results = await this.axios.get(this.oneRecipe + this.slug, {
        // in case there's headers needed, like for Django authentication
        // headers: {
        //   'Authorization': `token ${this.authToken}`
        // }
      });
      // Once results are in this.data, they're ready to use
      this.data = results.data;
    } catch (e) {
      console.log(e);
      this.error = "This resource is not loading";
    }

    this.loading = false;
  },
  methods: {
    editPageGo() {
      this.$router.push("/recipe/edit/" + this.data.slug);
    },
  },
};
</script>
