<template lang="">
     <section class="landing-hero pt-5">
      <div class="header__bg"></div>
      <div class="container mx-auto relative">
        <Navbar />
        <div class="flex items-center pt-10 px-5 md:px-0">
          <div class="w-1/2">
            <h1 class="text-4xl text-white mb-5">
              Platform Untuk Membantu<u class="hero-underline"> Petani</u>
              Mendapatkan<u class="hero-underline"> Akses Permodalan </u>
            </h1>

            <p class="text-white text-xl font-light mb-8">
              Mendanai projek yang terbaik untuk
              <br />
              mewujudkan mimpi mereka
            </p>
            <nuxt-link
              to='/allproject'
              class="
                block
                bg-orange-button
                hover:bg-green-button
                text-white
                font-semibold
                px-12
                py-3
                text-xl
                rounded-full
                text-center
                w-2/4
              "
            >
              Temukan Projek
            </nuxt-link>
          </div>
          <div class="w-1/2 flex justify-center">
            <img src="hero-image@2x.png" alt="crowdfunding project" />
          </div>
        </div>
      </div>
    </section>
</template>
<script>
export default {
    
}
</script>
<style lang="">
    
</style>