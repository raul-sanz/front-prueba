<template>
  <div class="lg:px-20 px-10 pt-2 mt-12 rounded-xl bg-gray-100">
    <div>
      <nuxt-link to="/"><button
        @click="$router.push('/')"
        class="py-2 px-6 bg-red-600 text-white rounded-full mb-4"
      >
        volver
      </button></nuxt-link>
    </div>
    <div class="bg-white rounded-lg p-2 shadow-lg">
      <div
        class="bg-local h-64 shadow-lg"
        :style="{
          backgroundImage: `url(${article.urlToImage})`,
          borderRadius: '25px',
        }"
      >
        <div class="py-2 px-4 w-full">
          <div class="flex mb-6">
            <div class="w-1/2">
              <vs-avatar size="50">
                <img src="https://vuesax.com/avatars/avatar-5.png" alt="" />
              </vs-avatar>
            </div>
            <div class="w-1/2 flex justify-end">
              <div>
                <p class="bg-red-400 rounded-full px-2 py-2 text-white">
                  {{ $moment(article.publishedAt).format("DD MMM YYYY") }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="w-full flex justify-center">
        <h4
          class="text-center font-semibold lg:text-2xl rounded-lg lg:px-6 mx-2 lg:mx-0 py-2"
        >
          {{ article.title }}
        </h4>
      </div>

      <div class="p-6">
        <p class="lg:text-2xl">{{ article.content }}</p>
      </div>
      <div class="w-full flex justify-end">
        <a :href="article.url" class="underline"
          >Puedes leer el post completo aqui</a
        >
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  computed: {
    ...mapState(["article"]),
  },
  created() {
    if (!this.article.title) {
      this.$router.push("/");
    }
  },
  transition: {
    name: "test",
    mode: "out-in",
  },
};
</script>

<style>
</style>