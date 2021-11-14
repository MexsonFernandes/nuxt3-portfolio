<template>
  <div>
    <NuxtLink to="/blog" class="text-sm text-blue-400">Go Back</NuxtLink><br />
    <main class="container relative px-4 mx-auto bg-white">
      <div class="relative -mx-4 top-0 pt-[17%] overflow-hidden">
        <img
          class="absolute inset-0 object-cover object-top w-full h-full  filter blur"
          :src="data[0].image.url"
          :alt="data[0].title"
        />
      </div>

      <div class="mt-[-10%] w-1/2 mx-auto">
        <div class="relative pt-[56.25%] overflow-hidden rounded-2xl">
          {{ data[0].image.url }}
          <img
            class="absolute inset-0 object-cover w-full h-full"
            :src="data[0].image.url"
            :alt="data[0].title"
          />
        </div>
      </div>

      <article class="py-8 mx-auto max-w-prose">
        <h1 class="text-2xl font-bold">
          {{ data[0].title }}
        </h1>
        <h2 class="mt-2 text-sm text-gray-500">{{ data[0].date }}</h2>
        <Markdown class="markdown" :source="data[0].content" />
      </article>
    </main>
  </div>
</template>

<script setup>
import { useRoute } from "vue-router";

const { params } = useRoute();
const { data } = await useFetch(
  `https://api.mexsonfernandes.com/articles?slug=${params.slug}`
);
if (data && data.value && data.value.length && data.value.length == 0) {
  window.location.href = "/blog";
}
</script>

<script>
import Markdown from "vue3-markdown-it";

export default {
  components: {
    Markdown,
  },
};
</script>

<style>
.markdown ul,
.markdown ol {
  list-style: disc;
  margin-left: 25px;
}
</style>
