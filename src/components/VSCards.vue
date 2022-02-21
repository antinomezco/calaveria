<template>
  <div v-if="items">
    <div class="grid grid-cols-12 gap-3 m-3 justify-items-center">
      <div v-for="item in items" :key="item.id" class="h-48 w-full rounded-lg relative col-span-12  md:col-span-6 md:col-span-4 lg:col-span-3 block max-w-sm bg-white shadow-md">
        <slot name="item" :item="item">
          <router-link :to="'/recipe/' + item.slug">
            <!-- pseudo image component contains all the code for dynamically showing the information in the database (item in items) -->
            <img
              class="object-cover h-full w-full rounded-lg"
              :src=item.image
              alt=""
            />
            <div class="absolute top-0 right-0">
              <div class="m-3 text-sm text-white bg-red-700 font-medium rounded-lg text-sm px-2 py-.5 text-center mr-2 mb-2">
                {{item.course.course_name}}
              </div>
            </div>
            <div class="title absolute inset-x-0 bottom-0">
              <div class="text-2xl font-bold text-white text-center">
                {{ item.recipe_name }}
              </div>
            </div>
          </router-link>
        </slot>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";

export default {
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="sass" scoped>
.title
  text-shadow: -1px 1px 0 #000, 1px 1px 0 #000, 1px -1px 0 #000, -1px -1px 0 #000
</style>
