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
            <h3 class="text-2xl text-gray-900 mb-4">Buat projek baru</h3>
          </div>
          <div class="w-1/4 text-right">
            <button
              @click="save"
              class="bg-green-button hover:bg-green-button text-white font-bold px-4 py-1 rounded inline-flex items-center"
            >
              Simpan
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
                      v-model="campaign.name"
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
                      v-model.number="campaign.goal_amount"
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
                      v-model="campaign.short_description"
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
                      v-model="campaign.perks"
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
                      placeholder="e.g :
                      Mengenal Vanili

                        Vanili merupakan tanaman yang buahnya bernilai ekonomi tinggi dan dapat digunakan sebagai bahan campuran makanan dan minuman. Vanili banyak digunakan sebagai bahan pembantu industri makanan dan pewangi obat-obatan, (flavour and fragrance ingredients). Sehingga, kebutuhannya cukup tinggi di pasaran.

                        Prospek Budidaya

                        Vanili merupakan salah satu komoditas ekspor rempah yang penting bagi peningkatan devisa negara. Permintaannya yang tinggi dan harga jual yang sangat tinggi di pasar lokal maupun internasional, juga salah satu faktor yang membuat vanili  menjadi menarik untuk dibudidayakan.

                        
                        Risiko Budidaya

                        Dalam budidaya vanili, kondisi lingkungan sangat menentukan sehingga dibutuhkan perlakuan yang khusus serta tepat agar resiko dapat ditekan. Daerah yang sesuai untuk budidaya vanili harus berada pada ketinggian 1-700 mdpl, bulan kering 2-4 bulan, temperatur 23-26 C, dan kelembaban 50-75%. Hama utama Vanili adalah bekicot dan ulat. Sedangkan untuk penyakit seringkali dijumpai Fusarium sp. dan Trichoderma sp. Baik untuk hama dan penyakit, pencegahan dan penanggulangan dini selalu dilakukan secara berkala.

                        Kelompok Tani Kami
                        Kelompok Tani Kami adalah kelompok tani yang sudah berdiri sejak tahun 2015. Kelompok tani ini memiliki lahan dengan luas total 2 hektar berlokasi di Jawa Tengah. Selama ini, mereka melakukan pembudidayaan vanili dengan modal sendiri. Namun sekarang bersama TaniFund, mereka berharap usaha pembudidayaan vanili mereka bisa berkembang dan dapat meningkatkan kesejahteraan masyarakat setempat dengan menyediakan peluang pekerjaan. Didasari dengan pertimbangan rekam jejak yang baik serta pengalaman budidaya kelompok tani ini, maka TaniFund tertarik untuk menjalin kerjasama dengan mereka."
                      v-model="campaign.description"
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
  middleware:'auth',
  
    data() {
      return {
        campaign: {
          name:'',
          short_description:'',
          description:'',
          goal_amount:'',
          perks:'',
        }
      }
    },

    methods: {
      async save() {
        try {
          let response = await this.$axios.$post('/api/v1/projek', this.campaign)
          this.$router.push({
            name : 'dashboard-projek-id',
            params:{id:response.data.id}
          })
          console.log(response);
        } catch (error) {
          console.log(error);
        }
      }
    },
}
</script>
<style lang="">
    
</style>