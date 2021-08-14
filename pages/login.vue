<template lang="">
    <div class="h-screen flex justify-center items-center">
        <div
          class="hidden md:block lg:w-1/3 bg-white h-full auth-background rounded-tr-lg rounded-br-lg"
        ></div>
        <div class="w-auto md:w-2/4 lg:w-2/3 flex justify-center items-center">
          <div class="w-full lg:w-1/2 px-10 lg:px-0">
            <h2 class="font-normal mb-6 text-3xl text-white">
              Masuk ke Akun Anda
            </h2>
            <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3"
              >Alamat Email</label
            >
            <input
              type="email"
              v-model="login.email"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Masukan alamat email"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3"
              >Password</label
            >
            <input
              @keyup.enter="userLogin"
              type="password"
              v-model="login.password"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Password"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <button
              @click="userLogin"
              class="block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full"
            >
              Login
            </button>
          </div>
        </div>
            <div class="text-center">
              <p class="text-white text-md">
                Belum punya akun ?
                <nuxt-link to="/daftar" class="no-underline text-orange-button">Daftar</nuxt-link>
              </p>
            </div>
          </div>
        </div>
      </div>
</template>
<script>
  // https://auth.nuxtjs.org/api/auth/#loginwithstrategyname-args
  // Scheme link : https://auth.nuxtjs.org/schemes/local/#usage

export default {
  layout: 'auth',
  data() {
    return {
      login: {
        email: '',
        password: '',
      },
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        this.$auth.setUser(response.data.data)
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.auth-background {
  background-image: url('/sign-in-background.jpg');
  background-position: center;
  background-size: cover;
}
</style>