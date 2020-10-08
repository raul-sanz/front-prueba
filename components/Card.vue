<template>
  <vs-card @click="viewArticle(article)" class="m-4">
    <template #title>
      <h3>{{ article.title }}</h3>
    </template>
    <template #img>
      <img :src="article.urlToImage" alt="" />
    </template>
    <template #text>
      <p>{{ article.content.split(" ").splice(0, 10).join(" ") + "\u2026" }}</p>
    </template>
    <template #interactions v-if="index % 2">
      <vs-button info icon>
        <i class="bx bx-heart"></i>
      </vs-button>
      <vs-button class="btn-chat" shadow secondary>
        <i class="bx bx-chat"></i>
        <span class="span"
          >{{ $moment(article.publishedAt).format("DD-MM-YYYY") }}
        </span>
      </vs-button>
    </template>
    <template #interactions v-else>
      <vs-button danger icon>
        <i class="bx bx-heart"></i>
      </vs-button>
      <vs-button class="btn-chat" shadow secondary>
        <i class="bx bx-chat"></i>
        <span class="span"
          >{{ $moment(article.publishedAt).format("DD-MM-YYYY") }}
        </span>
      </vs-button>
    </template>
  </vs-card>
</template>

<script>
import { mapMutations } from "vuex";
export default {
  name: "Card",
  props: ["article", "index"],
  methods: {
    ...mapMutations({ setArticle: "setArticle" }),
    viewArticle(item) {
      this.setArticle(item);
      this.$router.push(`/${item.title.replace(/ /g, "")}`);
    },
  },
};
</script>

<style>
</style>