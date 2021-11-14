<template>
  <div>
    <page-header title="Projects"></page-header>
    <div class="flex-grow min-h-screen px-10 pt-12 pb-12 bg-white-100">
      <div v-for="project in data" class="mt-5">
        <h3 class="mt-0 mb-2 text-4xl font-normal leading-normal">
          {{ project.title }}
        </h3>
        <h3 class="mt-0 mb-2 text-2xl font-normal leading-normal">
          <Markdown :source="project.subtitle" />
        </h3>
        <div class="markdown">
          <Markdown :source="project.description" />
        </div>

        <div
          v-if="
            project.Techstack &&
            project.Techstack.length &&
            project.Techstack.length > 0
          "
        >
          <br />
          <span class="font-bold">Tech Stack</span>
          <div class="flex flex-wrap">
            <div
              class="w-12 m-1 flex-4 has-tooltip"
              v-for="icon in project.Techstack"
            >
              <div class="relative flex flex-col items-center group">
                <div class="w-12 h-12">
                  <img
                    class="m-1 grayscale hover:grayscale-0"
                    :alt="icon.stack"
                    :src="icon.logo.url"
                  />
                </div>
                <div
                  class="absolute bottom-0 flex flex-col items-center hidden mb-6  group-hover:flex"
                >
                  <span
                    class="relative z-10 p-2 text-xs leading-none text-white whitespace-no-wrap bg-black shadow-lg "
                    >{{ icon.stack }}</span
                  >
                  <div class="w-3 h-3 -mt-2 rotate-45 bg-black"></div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div
          v-if="project.Team && project.Team.length && project.Team.length > 0"
        >
          <br />
          <span class="font-bold">Team</span>
          <div class="flex flex-wrap">
            <div class="m-1 flex-4 has-tooltip" v-for="icon in project.Team">
              <div class="relative flex flex-col items-center group">
                <div class="w-12 h-12">
                  <img
                    class="m-1 rounded-full grayscale hover:grayscale-0"
                    :alt="icon.photo.caption"
                    :src="icon.photo.url"
                  />
                </div>
                <div
                  class="absolute bottom-0 flex flex-col items-center hidden mb-12  group-hover:flex"
                >
                  <span
                    class="relative z-10 p-1 text-xs leading-none text-white whitespace-no-wrap bg-black shadow-lg "
                    >{{ icon.photo.caption }}</span
                  >
                  <div class="w-3 h-3 -mt-2 rotate-45 bg-black"></div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div
          v-if="
            project.Action && project.Action.length && project.Action.length > 0
          "
        >
          <br />
          <span class="font-bold">Links</span>
          <div class="flex flex-wrap">
            <div class="w-8 h-8 m-1 flex-4" v-for="action in project.Action">
              <a
                :aria-label="action.link"
                rel="noopener"
                class="rounded-full"
                target="_blank"
                :href="action.link"
                ><img
                  class="rounded-full grayscale hover:grayscale-0"
                  :src="`${action.logo.url}`"
              /></a>
            </div>
          </div>
        </div>

        <div class="mt-5"></div>

        <hr
          class="text-2xl text-center border-black"
          data-hr-content="Title"
          style="--bg: white; --p: 0 10px; --trans-x: -50%; --trans-y: -50%"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
const { data } = await useFetch(
  `https://api.mexsonfernandes.com/projects?_sort=started`
);
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
