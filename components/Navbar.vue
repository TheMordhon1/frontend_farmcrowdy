<template lang="">
  <header class="flex items-center">
    <div style="height: 54px" class="pr-5">
      <img src="/logo.svg" alt="logo" class="h-full" />
    </div>
    <ul class="flex items-center">
      <li>
        <a
          class="text-white hover:text-teal-500 text-lg px-4 py-3"
          href="/"
          >Home</a
        >
      </li>
      <li>
        <a
          class="text-white hover:text-teal-500 text-lg px-4 py-3"
          href="projects.html"
          >Projek</a
        >
      </li>
      <li>
        <a
          class="text-white hover:text-teal-500 text-lg px-4 py-3"
          href="features.html"
          >Fitur</a
        >
      </li>
      <li>
        <a
          class="text-white hover:text-teal-500 text-lg px-4 py-3"
          href="story.html"
          >Kisah Sukses</a
        >
      </li>
    </ul>
    <ul class="flex ml-auto items-center mt-2">
      <li>
        <nuxt-link
          to="daftar"
          class="
            inline-block
            bg-transparent
            border-white border
            hover:bg-white hover:bg-opacity-25
            text-white
            font-light
            w-40
            text-center
            px-6
            py-1
            text-lg
            rounded-full
            mr-4
          "
        >
          Daftar
        </nuxt-link>
      </li>
      <li>
        <nuxt-link
          to="login"
          class="
            inline-block
            bg-transparent
            border-white border
            hover:bg-white hover:bg-opacity-25
            text-white
            font-light
            w-40
            text-center
            px-6
            py-1
            text-lg
            rounded-full
          "
        >
          Masuk
        </nuxt-link>
      </li>
    </ul>
  </header>
</template>
<script>
export default {}
</script>
<style lang=""></style>
