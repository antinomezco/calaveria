<template>
  <div class="header">
    <div class="recipe-hero">
      <!-- b-back, bg and ui are in 3 separate, but combined layers, on top of each other, check css for details  -->
      <div class="bg-back"></div>
      <div
        class="bg"
        style="background-image: url('https://images.unsplash.com/photo-1523986371872-9d3ba2e2a389?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8c3VtbWVyJTIwZm9vZHxlbnwwfHwwfHw%3D&ixlib=rb-1.2.1&w=1000&q=80');"
      ></div>
      <div class="ui-container">
        <div class="flex justify-between p-5">
          <img class="h-20" src="../assets/chef.png"/>
          <ul class="h-10 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900 ">
            <li v-if="!$auth.isAuthenticated" @click="login">Log in/Sign up</li>
            <li v-else @click="logout">Log out</li>
          </ul>
        </div>
        <div class="px-5 text-left text-white w-full sm:w-4/5 md:w-2/3 lg:w-1/2">
          <div class="text-xl space-y-2">
            <p class="text-3xl">
              La calavería
            </p>
            <p class="desc">
              Inspired by <span class="underline"><a href="http://www.theskullery.net">The Skullery</a></span>
              as to combine several of my passions, web development, photography and cooking.
            </p>
            <p class="desc">
              This is a website created to test my abilities as a web developer.
              The frontend is made with VueJS using CSS and Tailwind. In addition the following packages are used: firebase (for 
              storing images), auth0 (for authentication), lodash (for its 
              debounce function), vee-validate (for forms), axios (to connect 
              to my own API) and vue-router (to navigate between different pages
              and for authentication guard with auth0).
            </p>
            <p class="desc">
              The backend was made from scratch using Django, custom made for this
              particular website.
            </p>
            <p class="invert">
              <img
                class="w-20"
                src="../assets/quill-drawing-a-line.png"
              />
            </p>
            <div class="py-5">
              <router-link to="/addrecipe" class="text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900 ">
                Submit Recipe
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    login() {
      this.$auth.loginWithRedirect();
    },
    logout() {
      this.$auth.logout();
      this.$router.push({ path: "/" });
    },
  },
};
</script>

<style lang="sass" scoped>
// Main component css

.recipe-hero
  position: relative

// Layered image and color transparency

.bg
  background-repeat: no-repeat
  background-attachment: center
  background-position: center
  background-size: cover
  top: 0
  left: 0
  width: 100%
  height: 100%
  position: absolute
  mix-blend-mode: multiply
  filter: grayscale(100%)
.bg-back
  background: red
  width: 100%
  height: 100%
  top: 0
  left: 0
  position: absolute

// Images and text in header

.ui-container
  display: inline-block
  // width: 100%
  position: relative

p
  text-shadow: -1px 1px 0 #000, 1px 1px 0 #000, 1px -1px 0 #000, -1px -1px 0 #000

</style>
