<template>
  <footer class="footer justify-center flex py-2 text-left">
    <div class="w-5/6 sm:4/5 md:w-3/4">
      <div class="upper flex grid grid-cols-12 gap-3 pb-3">
        <div class="about space-y-2 md:pr-5 col-span-12 lg:col-span-8">
          <b class="text-xl">About</b>
          <p>
            This footer doesn't have any actual function, it just makes the
            website look better by having it. In addition, the links to the side
            don't actually work, they're currently placeholders to show how they
            could look. If needed, I could extend the functionality of the
            website to include such things, but this is just a simple show of a
            CRUD website at the moment. For the next paragraph, I'll just repeat
            whatever I put in the header:
          </p>
          <p>
            This is a website created to test my abilities as a web developer.
            The frontend is made made with VueJS without using any component
            library, just CSS. In addition the following packages are used:
            dotenv (for storing environmental variables), firebase (for storing
            images), auth0 (for authentication), lodash (for its debounce
            function), vee-validate (for forms), axios (to connect to my own
            API) and vue-router (to navigate between different pages and for
            authentication guard with auth0).
          </p>
        </div>
        <div class="flex flex-row grid col-span-12 grid-cols-2 lg:col-span-4 text-slate-100 gap-3 leading-snug"
        >
          <div>
            <b class="text-xl">Links</b>
            <ul>
              <li>Stats</li>
              <li>Contact</li>
              <li>Privacy</li>
              <li>Favorites</li>
            </ul>
          </div>
          <div>
            <b class="text-xl">Site</b>
            <ul>
              <li>Categories</li>
              <li>Cuisines</li>
              <li>Chefs</li>
              <li>Meals</li>
            </ul>
          </div>
        </div>
      </div>
      <hr />
      <div
        class="text-slate-100 font-bold text-sm leading-snug grid-rows-1"
      >
        <p>
          Website design inspired by
          <a target="_blank" href="http://theskullery.net" class="underline"
            >theskullery.net</a
          >
        </p>
        <p>It was made, with effort</p>
        <p>
          Constantino Saldana, at
          <a target="_blank" href="http://csaldana.xyz" class="underline"
            >csaldana.xyz</a
          >
        </p>
      </div>
    </div>
  </footer>
</template>

<style lang="sass" scoped>

//Main component css
.footer
  border-top: solid 2px darkred
  background-color: #ffffff
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='400' viewBox='0 0 200 200'%3E%3Cg fill='none' stroke='%23000000' stroke-width='1' stroke-opacity='0.05'%3E%3Crect x='-40' y='40' width='75' height='75'/%3E%3Crect x='-35' y='45' width='65' height='65'/%3E%3Crect x='-30' y='50' width='55' height='55'/%3E%3Crect x='-25' y='55' width='45' height='45'/%3E%3Crect x='-20' y='60' width='35' height='35'/%3E%3Crect x='-15' y='65' width='25' height='25'/%3E%3Crect x='-10' y='70' width='15' height='15'/%3E%3Crect x='-5' y='75' width='5' height='5'/%3E%3Crect width='35' height='35'/%3E%3Crect x='5' y='5' width='25' height='25'/%3E%3Crect x='10' y='10' width='15' height='15'/%3E%3Crect x='15' y='15' width='5' height='5'/%3E%3Crect x='40' width='75' height='75'/%3E%3Crect x='45' y='5' width='65' height='65'/%3E%3Crect x='50' y='10' width='55' height='55'/%3E%3Crect x='55' y='15' width='45' height='45'/%3E%3Crect x='60' y='20' width='35' height='35'/%3E%3Crect x='65' y='25' width='25' height='25'/%3E%3Crect x='70' y='30' width='15' height='15'/%3E%3Crect x='75' y='35' width='5' height='5'/%3E%3Crect x='40' y='80' width='35' height='35'/%3E%3Crect x='45' y='85' width='25' height='25'/%3E%3Crect x='50' y='90' width='15' height='15'/%3E%3Crect x='55' y='95' width='5' height='5'/%3E%3Crect x='120' y='-40' width='75' height='75'/%3E%3Crect x='125' y='-35' width='65' height='65'/%3E%3Crect x='130' y='-30' width='55' height='55'/%3E%3Crect x='135' y='-25' width='45' height='45'/%3E%3Crect x='140' y='-20' width='35' height='35'/%3E%3Crect x='145' y='-15' width='25' height='25'/%3E%3Crect x='150' y='-10' width='15' height='15'/%3E%3Crect x='155' y='-5' width='5' height='5'/%3E%3Crect x='120' y='40' width='35' height='35'/%3E%3Crect x='125' y='45' width='25' height='25'/%3E%3Crect x='130' y='50' width='15' height='15'/%3E%3Crect x='135' y='55' width='5' height='5'/%3E%3Crect y='120' width='75' height='75'/%3E%3Crect x='5' y='125' width='65' height='65'/%3E%3Crect x='10' y='130' width='55' height='55'/%3E%3Crect x='15' y='135' width='45' height='45'/%3E%3Crect x='20' y='140' width='35' height='35'/%3E%3Crect x='25' y='145' width='25' height='25'/%3E%3Crect x='30' y='150' width='15' height='15'/%3E%3Crect x='35' y='155' width='5' height='5'/%3E%3Crect x='200' y='120' width='75' height='75'/%3E%3Crect x='40' y='200' width='75' height='75'/%3E%3Crect x='80' y='80' width='75' height='75'/%3E%3Crect x='85' y='85' width='65' height='65'/%3E%3Crect x='90' y='90' width='55' height='55'/%3E%3Crect x='95' y='95' width='45' height='45'/%3E%3Crect x='100' y='100' width='35' height='35'/%3E%3Crect x='105' y='105' width='25' height='25'/%3E%3Crect x='110' y='110' width='15' height='15'/%3E%3Crect x='115' y='115' width='5' height='5'/%3E%3Crect x='80' y='160' width='35' height='35'/%3E%3Crect x='85' y='165' width='25' height='25'/%3E%3Crect x='90' y='170' width='15' height='15'/%3E%3Crect x='95' y='175' width='5' height='5'/%3E%3Crect x='120' y='160' width='75' height='75'/%3E%3Crect x='125' y='165' width='65' height='65'/%3E%3Crect x='130' y='170' width='55' height='55'/%3E%3Crect x='135' y='175' width='45' height='45'/%3E%3Crect x='140' y='180' width='35' height='35'/%3E%3Crect x='145' y='185' width='25' height='25'/%3E%3Crect x='150' y='190' width='15' height='15'/%3E%3Crect x='155' y='195' width='5' height='5'/%3E%3Crect x='160' y='40' width='75' height='75'/%3E%3Crect x='165' y='45' width='65' height='65'/%3E%3Crect x='170' y='50' width='55' height='55'/%3E%3Crect x='175' y='55' width='45' height='45'/%3E%3Crect x='180' y='60' width='35' height='35'/%3E%3Crect x='185' y='65' width='25' height='25'/%3E%3Crect x='190' y='70' width='15' height='15'/%3E%3Crect x='195' y='75' width='5' height='5'/%3E%3Crect x='160' y='120' width='35' height='35'/%3E%3Crect x='165' y='125' width='25' height='25'/%3E%3Crect x='170' y='130' width='15' height='15'/%3E%3Crect x='175' y='135' width='5' height='5'/%3E%3Crect x='200' y='200' width='35' height='35'/%3E%3Crect x='200' width='35' height='35'/%3E%3Crect y='200' width='35' height='35'/%3E%3C/g%3E%3C/svg%3E")
  /* background by SVGBackgrounds.com */

.about
  position: relative
  p
    position: relative
    line-height: 1.5
    font-size: .8rem
  &::before // hat image behing the text with opacity
    content: ''
    position: absolute
    top: 0
    right: 0
    bottom: 0
    left: 0
    opacity: 0.3
    background-image: url("../assets/chef.png")
    background-repeat: no-repeat
    background-position: center
    background-size: 100px 100px
</style>
