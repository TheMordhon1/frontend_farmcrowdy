<template>
  <div class="project-page">
    <section class="project-header pt-5">
      <div class="container mx-auto relative">
        <Navbar />
      </div>
    </section>
    <section class="container project-container mx-auto -mt-56">
      <div class="flex mt-3">
        <div class="w-3/4 mr-6">
          <div class="bg-white p-3 mb-3 border border-gray-400 rounded-20">
            <figure class="item-image">
              <img :src="default_image" alt="" class="rounded-20  w-max max-h-66" />
            </figure>
          </div>
          <div class="flex -mx-2">
            <div
              v-for="image in campaign.data.images"
              :key="image.image_url"
              class="
                relative
                w-1/4
                bg-white
                m-2
                p-2
                border border-gray-400
                rounded-20
              "
            >
              <figure class="item-thumbnail cursor-pointer">
                <img
                  :src="$axios.defaults.baseURL + '/' + image.image_url"
                  @click="
                    changeImage($axios.defaults.baseURL + '/' + image.image_url)
                  "
                  alt=""
                  class="rounded-20 w-full"
                />
              </figure>
            </div>
          </div>
        </div>
        <div class="w-1/4">
          <div
            class="bg-white w-full p-5 border border-gray-400 rounded-20 sticky"
            style="top: 15px"
          >
            <h3>Pembuat projek:</h3>

            <div class="flex mt-3">
              <div class="w-1/4">
                <img
                  :src="
                    $axios.defaults.baseURL + '/' + campaign.data.user.image_url
                  "
                  alt=""
                  class="w-full inline-block rounded-full h-16"
                />
              </div>
              <div class="w-3/4 ml-5 mt-1">

                <div class="font-semibold text-xl text-gray-800">
                {{ campaign.data.user.name }} </div>
                <div class="text-sm  text-gray-800">
                ({{ campaign.data.user.occupation }})</div>
                
                <div class="font-light text-md text-gray-400 mt-2">
                  {{ campaign.data.backer_count }} Funder
                </div>
              </div>
            </div>

            <h4 class="mt-5 font-semibold">Yang akan anda dapatkan:</h4>
            <ul class="list-check mt-3">
              <li v-for="perk in campaign.data.perks" :key="perk">
                {{ perk }}
              </li>
            </ul>
            <template v-if="this.$store.state.auth.loggedIn">
              <input
                type="number"
                class="
                  border border-gray-500
                  block
                  w-full
                  px-6
                  py-3
                  mt-4
                  rounded-full
                  text-gray-800
                  transition
                  duration-300
                  ease-in-out
                  focus:outline-none
                  focus:shadow-outline
                "
                placeholder="Jumlah Dalam Rp"
                v-model.number="transactions.amount"
                @keyup.enter="fund"
              />
              <button
                @click="fund"
                class="
                  mt-3
                  button-cta
                  block
                  w-full
                  bg-orange-button
                  hover:bg-green-button
                  text-white
                  font-medium
                  px-6
                  py-3
                  text-md
                  rounded-full
                "
              >
                Bantu Sekarang
              </button>
            </template>
            <template v-else>
              <button
                @click="$router.push({ path: '/login' })"
                class="
                  mt-3
                  button-cta
                  block
                  w-full
                  bg-orange-button
                  hover:bg-green-button
                  text-white
                  font-medium
                  px-6
                  py-3
                  text-md
                  rounded-full
                "
              >
                Bantu Sekarang
              </button>
            </template>
          </div>
        </div>
      </div>
    </section>
    <section class="container mx-auto pt-8">
      <div class="flex justify-between items-center">
        <div class="w-full md:w-3/4 mr-6">
          <h2 class="text-4xl text-gray-900 mb-2 font-medium">
            {{ campaign.data.name }}
          </h2>
          <p class="font-light text-xl mb-5">
            {{ campaign.data.short_description }}
          </p>

          <div class="relative progress-bar">
            <div
              class="overflow-hidden mb-4 text-xs flex rounded-full bg-gray-200 h-6"
            >
              <div
                :style="
                  'width: ' +
                  (campaign.current_amount / campaign.goal_amount) * 100 +
                  '%'
                "
                class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
              ></div>
            </div>
          </div>
          <div class="flex progress-info mb-6">
            <div class="text-2xl">
              {{
                parseFloat(campaign.data.current_amount / campaign.data.goal_amount).toFixed(2) *
                100
              }}%
              
            </div>
            <div class="ml-auto font-semibold text-2xl"> <span class="text-sm font-normal mr-2">sampai</span>
              Rp {{ new Intl.NumberFormat().format(campaign.data.goal_amount) }}
            </div>
          </div>

          <p class="font-light text-xl mb-5 whitespace-pre-line">
            {{ campaign.data.description }}
          </p>
        </div>
        <div class="w-1/4 hidden md:block"></div>
      </div>
    </section>
    <div class="cta-clip -mt-20"></div>
    <CallToAction />
    <Footer />
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const campaign = await $axios.$get('/api/v1/projek/' + params.id)
    return { campaign }
  },
  data() {
    return {
      default_image: '',
      transactions: {
        amount: 0,
        campaign_id: Number.parseInt(this.$route.params.id),
      },
    }
  },
  methods: {
    async fund() {
      try {
        let response = await this.$axios.$post(
          '/api/v1/transaksi',
          this.transactions
        )
        window.location = response.data.payment_url
        console.log(response.data.payment_url)
      } catch (error) {
        console.log(error)
      }
    },
    changeImage(url) {
      this.default_image = url
    },
  },
  mounted() {
    this.default_image =
      this.$axios.defaults.baseURL + '/' + this.campaign.data.image_url
  },
}
</script>

<style lang="scss">

</style>
