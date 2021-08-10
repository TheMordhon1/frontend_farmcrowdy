<template lang="">
    <div class="h-screen flex justify-center items-center">
        <div
          class="hidden md:block lg:w-1/3 bg-white h-full auth-background rounded-tr-lg rounded-br-lg"
        ></div>
        <div class="w-auto md:w-2/4 lg:w-2/3 flex justify-center items-center">
          <div class="w-full lg:w-1/2 px-10 lg:px-0">
            <h2 class="font-normal mb-6 text-3xl text-white">
              Buat Akun
            </h2>
            <div class="mb-6">
              <div class="mb-4">
                <label class="font-normal text-lg text-white block mb-3"
                  >Nama Lengkap</label
                >
                <input
                  type="text"
                  class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
                  placeholder="ex: Ardi Saputra"
                />
              </div>
            </div>
            <div class="mb-6">
              <div class="mb-4">
                <label class="font-normal text-lg text-white block mb-3"
                  >Pekerjaan</label
                >
                <input
                  type="text"
                  class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
                  placeholder="ex: Pengusaha"
                />
              </div>
            </div>
            <div class="mb-6">
              <div class="mb-4">
                <label class="font-normal text-lg text-white block mb-3"
                  >Alamat Email</label
                >
                <input
                  type="email"
                  class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
                  placeholder="ex: ardisapt@gmail.com"
                />
              </div>
            </div>
            <div class="mb-6">
              <div class="mb-4">
                <label class="font-normal text-lg text-white block mb-3"
                  >Password</label
                >
                <input
                  type="password"
                  class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
                  placeholder="Masukan Password Anda"
                />
              </div>
            </div>
            <div class="mb-6">
              <div class="mb-4">
                <button
                  @click="$router.push({ path: '/upload' })"
                  class="block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full"
                >
                  Lanjutkan
                </button>
              </div>
            </div>
            <div class="text-center">
              <p class="text-white text-md">
                Sudah punya akun?
                <nuxt-link to="/login" class="no-underline text-orange-button"
                  >Log In</nuxt-link>
              </p>
            </div>
          </div>
        </div>
      </div>
</template>
<script>
export default {
    layout: 'auth'
}
</script>
<style scoped>
    .auth-background {
        background-image: url("/sign-up-background.jpg");
        background-position: center;
        background-size: cover;
      }
</style>