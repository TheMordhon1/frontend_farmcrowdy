<template lang="">
    <div class="project-page">
      <section class="dashboard-header pt-5">
        <div class="container mx-auto relative">
          <Navbar/>
        </div>
      </section>
      
      <section class="container mx-auto pt-8">
        <div class="flex justify-between items-center">
          <div class="w-full mr-6">
            <h2 class="text-4xl text-gray-900 mb-2 font-medium">Dashboard</h2>
          </div>
        </div>
        <div class="flex justify-between items-center">
          <div class="w-3/4 mr-6">
            <h3 class="text-2xl text-gray-900 mb-4 capitalize">edit projek "{{campaign.data.name}}"</h3>
          </div>
          <div class="success" v-if="savingSuccessful"> 
              Berhasil di ubah 
          </div>
        
          <div class="w-1/4 text-right">
            <button
              @click="save"
              class="bg-green-button hover:bg-green-button text-white font-bold px-4 py-1 rounded inline-flex items-center"
              v-if="!savingSuccessful"
            >
              Ubah
            </button>
          </div>
        </div>
        <div class="block mb-2">
          <div class="w-full lg:max-w-full lg:flex mb-4">
            <div
              class="w-full border border-gray-400 bg-white rounded p-8 flex flex-col justify-between leading-normal"
            >
              <form class="w-full">
                <div class="flex flex-wrap -mx-3 mb-6">
                  <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
                    <label
                      class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                    >
                      Nama Projek
                    </label>
                    <input
                      class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                      type="text"
                      placeholder="ex: Projek Porang Pak Dudi"
                      v-model="campaign.data.name"
                    />
                  </div>
                  <div class="w-full md:w-1/2 px-3">
                    <label
                      class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                    >
                      Total Biaya Projek
                    </label>
                    <input
                      class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                      type="number"
                      placeholder="ex: 60000000"
                      v-model.number="campaign.data.goal_amount"
                    />
                  </div>
                  <div class="w-full px-3">
                    <label
                      class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 mt-3"
                    >
                      Keterangan Singkat
                    </label>
                    <input
                      class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                      type="text"
                      placeholder="Deskripsi singkat mengenai projectmu"
                      v-model="campaign.data.short_description"
                    />
                  </div>
                  <div class="w-full px-3">
                    <label
                      class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                    >
                      Yang anda tawarkan kepada funder
                    </label>
                    <input
                      class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                      type="text"
                      placeholder="*jika lebih dari satu pisahkan dengan tanda koma (,)"
                      v-model="campaign.data.perks"
                    />
                  </div>
                  <div class="w-full px-3">
                    <label
                      class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                    >
                      Deskripsi Projek
                    </label>
                    <textarea rows="14"
                      class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                      type="text"
                      placeholder="Isi deskripsi projekmu dengan jelas dan detail"
                      v-model="campaign.data.description"
                    ></textarea>
                  </div>
                </div>
              </form>
            </div>
          </div>
        </div>
      </section>
      <div class="cta-clip -mt-20"></div>
      <CallToAction/>
      <Footer/>
    </div>
</template>
<script>
export default {
  middleware: 'auth',
  async asyncData({ $axios, params }) {
    const campaign = await $axios.$get('/api/v1/campaigns/' + params.id)
    return { campaign }
  },
  methods: {
    
    async save() {
      try {
        var savingSuccessful = false
        let response = await this.$axios.$put(
          '/api/v1/campaigns/' + this.$route.params.id,
          {
            name: this.campaign.data.name,
            short_description: this.campaign.data.short_description,
            description: this.campaign.data.description,
            goal_amount: this.campaign.data.goal_amount,
            perks: this.campaign.data.perks.join(),
          }
        )
        console.log(response, savingSuccessful)
      } catch (err) {
        console.log(err)
      }
    },
    changeImage(url) {
      this.default_image = url
    },
  },
}
</script>
<style lang="">
    
</style>