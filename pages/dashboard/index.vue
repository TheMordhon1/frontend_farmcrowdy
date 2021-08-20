<template lang="">
    <div class="project-page">
      <section class="dashboard-header pt-5">
        <div class="container mx-auto relative">
          <Navbar/>
        </div>
      </section>
      <section class="container mx-auto pt-8">
        <div class="flex justify-between items-center mb-6">
          <div class="w-3/4 mr-6">
            <h2 class="text-4xl text-gray-900 mb-2 font-medium">Dashboard</h2>
            <ul class="flex mt-2">
              <li class="mr-6">
                <a class="text-gray-800 font-bold" href="#"> Projek Anda </a>
              </li>
              <li class="mr-6">
                <nuxt-link
                  class="text-gray-500 hover:text-gray-800"
                  to="/dashboard/transaksi"
                >
                  Riwayat Transaksi
                </nuxt-link>
              </li>
            </ul>
          </div>
          <div class="w-1/4 text-right">
          <nuxt-link to="/dashboard/projek/create" class="bg-orange-button hover:bg-green-button text-white font-bold py-4 px-4 rounded inline-flex items-center"> + Buat Projek</nuxt-link>
          </div>
        </div>
        <hr />
        <div class="block mb-2">
          <div class="w-full lg:max-w-full lg:flex mb-4" v-for="campaign in projek.data" :key="campaign.id">
            <div
              class="border h-48 lg:h-auto lg:w-64 flex-none bg-cover rounded-t lg:rounded-t-none lg:rounded-l text-center overflow-hidden"
            :style="
              'background-color: #bbb; background-position: center; background-image: url(\'' +
              $axios.defaults.baseURL +
              '/' +
              campaign.image_url +
              '\')'
            "
            ></div>
            <nuxt-link
            :to="'/dashboard/projek/' + campaign.id"
              class=" w-full border-r border-b border-l border-gray-400 lg:border-l-0 lg:border-t lg:border-gray-400 bg-white rounded-b lg:rounded-b-none lg:rounded-r p-8 flex flex-col justify-between leading-normal"
            >
              <div class="mb-8">
                <div class="text-gray-900 font-bold text-xl mb-1">
                  {{campaign.name}}
                </div>
                <p class="text-sm text-gray-600 flex items-center mb-2">
                  {{ parseFloat(campaign.current_amount / campaign.goal_amount).toFixed(2) * 100 }}% /
                  Rp.  {{ new Intl.NumberFormat().format(campaign.goal_amount) }}
                &middot;
                terakhir di ubah pada {{  new Date(campaign.updated_at) | dateFormat('DD/MM/YYYY, hh:mm a') }}
                
                </p>
                <p class="text-gray-700 text-base">
                  {{ campaign.short_description }}
                </p>
              </div>
              <div class="flex items-center">
                <nuxt-link
                  :to="'/dashboard/projek/' + campaign.id"
                  class="bg-green-button text-white py-2 px-4 rounded"
                >
                  Detail
                </nuxt-link>
              </div>
            </nuxt-link>
          </div>
        </div>
      </section>
      <div class="cta-clip -mt-20"></div>
      <section class="call-to-action bg-purple-progress pt-64 pb-10"></section>
      <Footer/>
    </div>
</template>
<script>
import Vue from 'vue';
import VueFilterDateFormat from 'vue-filter-date-format';

Vue.use(VueFilterDateFormat);
export default {
      middleware: 'auth',
      async asyncData({ $axios, app}) {
        const projek = await $axios.$get('/api/v1/projek?user_id=' + app.$auth.user.id)
      return {projek}
      }
}
</script>
<style lang="">
    
</style>