<template lang="">
    <div class="success-page">
      <div class="container mx-auto h-screen flex justify-center items-center">
        <div class="w-full lg:w-1/3 px-10 lg:px-0">
          <div class="flex justify-center items-center mx-auto mt-6 mb-8">
            <img src="/funded-illustration.svg" alt="" class="w-full" />
          </div>
          <h2 class="font-medium mb-3 text-3xl text-center">
            Maaf, transaksi anda gagal!
          </h2>
          <p class="text-center font-light">
           Silahkan lakukan kembali proses transaksi
          </p>
          <div class="mb-4 mt-6">
            <div class="mb-3">
              <button
                @click="$router.push({ path: '/' })"
                class="block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full"
              >
                Coba lagi
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
