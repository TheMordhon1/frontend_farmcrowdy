<template lang="">
  <section class="call-to-action bg-purple-progress pt-64 pb-10">
    <div class="container mx-auto">
      <div class="w-full text-center">
        <h1 class="text-5xl text-white font-semibold">
          Membantu Petani
          <br />
          untuk Maju
        </h1>
        <button
          @click="$router.push({ path: '/upload' })"
          class="
            inline-block
            bg-orange-button
            hover:bg-green-button
            text-white
            font-semibold
            px-6
            py-4
            mt-8
            text-lg
            rounded-full
          "
        >
          Mulai Sekarang
        </button>
      </div>
    </div>
  </section>
</template>
<script>
export default {}
</script>
<style lang=""></style>
