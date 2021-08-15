<template>
  <div class="landing-page">
    <section class="dashboard-header pt-5">
        <div class="container mx-auto relative">
          <Navbar/>
        </div>
      </section>
    <section class="container mx-auto pt-24" id="project">
      <div class="flex justify-between items-center">
        <div class="w-auto">
          <h2 class="text-xl text-gray-900 mb-8">
            Projek Terbaru yang
            <br />
            Memerlukan Bantuan
          </h2>
        </div>
      
      </div>
      <div class="grid grid-cols-3 gap-4 mt-3">
        <div
          v-for="campaign in campaigns.data"
          :key="campaign.id"
          class="card-project w-full py-8 px-5 border border-gray-500 rounded-20"
        >
          <div class="item flex flex-col">
            <figure class="item-image">
              <img
                :src="$axios.defaults.baseURL + '/' + campaign.image_url"
                alt=""
                class="rounded-20"
              />
            </figure>
            <div class="item-meta">
              <h4 class="text-xl font-medium text-gray-900 mt-5">
                {{ campaign.name }}
              </h4>
              <p class="text-md font-light text-gray-900 h-12">
                {{ campaign.short_description }}
              </p>
              <div class="relative pt-4 progress-bar">
                <div
                  class="
                    overflow-hidden
                    h-2
                    mb-4
                    text-xs
                    flex
                    rounded
                    bg-gray-200
                    h-3
                    rounded-lg
                  "
                >
                  <div
                    :style="
                      'width: ' +
                      (campaign.current_amount / campaign.goal_amount) * 100 +
                      '%'
                    "
                    class="
                      shadow-none
                      flex flex-col
                      text-center
                      whitespace-nowrap
                      text-white
                      justify-center
                      bg-purple-progress
                      progress-striped
                    "
                  ></div>
                </div>
              </div>
              <div class="flex progress-info">
                <div>
                  {{ parseFloat(campaign.current_amount / campaign.goal_amount).toFixed(2) * 100 }}%
                </div>
                <div class="ml-auto font-semibold">
                  Rp {{ new Intl.NumberFormat().format(campaign.goal_amount) }}
                </div>
              </div>
            </div>
            <button
              @click="
                $router.push({
                  name: 'projects-id',
                  params: { id: campaign.id },
                })
              "
              class="
                mt-5
                button-cta
                block
                w-full
                bg-orange-button
                hover:bg-green-button
                text-white
                font-semibold
                px-6
                py-2
                text-lg
                rounded-full
              "
            >
              Bantu Projek Ini
            </button>
            <p class="mt-2"><span class="font-light text-gray-900"> terakhir di update pada </span>{{  new Date(campaign.updated_at) | dateFormat('DD/MM/YYYY, hh:mm a') }}</p>
          </div>
        </div>
      </div>
    </section>
    <div class="cta-clip -mt-20"></div>
    <CallToAction />
    <Footer />
  </div>
</template>

<script>
import Vue from 'vue';
import VueFilterDateFormat from 'vue-filter-date-format';
import Story from '~/components/Story.vue';

Vue.use(VueFilterDateFormat);
export default {
  components: { Story },
  async asyncData({ $axios }) {
    const campaigns = await $axios.$get('/api/v1/campaigns')
    return { campaigns }
  },
}
</script>
