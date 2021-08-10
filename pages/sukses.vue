<template lang="">
    <div class="success-page">
      <div class="container mx-auto h-screen flex justify-center items-center">
        <div class="w-full lg:w-1/3 px-10 lg:px-0">
          <div class="flex justify-center items-center mx-auto mt-6 mb-8">
            <img src="/funded-illustration.svg" alt="" class="w-full" />
          </div>
          <h2 class="font-medium mb-3 text-3xl text-center">
            Terimakasih, Orang Baik !
          </h2>
          <p class="text-center font-light">
            Dana akan diserahkan jika 
            <br />
            sudah terkumpul 100%
          </p>
          <div class="mb-4 mt-6">
            <div class="mb-3">
              <button
                @click="$router.push({ path: '/' })"
                class="block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full"
              >
                Bantu Projek Lainnya
              </button>
            </div>
            <div class="mb-4">
              <button
                @click="$router.push({ path: '/dashboard' })"
                class="block w-full bg-transparent border border-gray-500 text-gray-500 hover:bg-green-button hover:border-green-button hover:text-white font-light px-6 py-4 text-lg rounded-full"
              >
                Lihat Dashboard
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>
<script>
export default {
    layout: 'success'
}
</script>
