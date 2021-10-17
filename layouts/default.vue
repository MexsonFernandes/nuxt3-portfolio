<template>
  <div class="flex h-screen bg-gray-100">
    <div class="w-56 overflow-hidden bg-white">
      <div class="flex flex-wrap justify-center p-4">
        <img
          class="object-cover align-middle rounded-full h-28 w-28 drop-shadow-lg"
          src="~/assets/images/mexson.png"
          alt="Mexson Fernandes"
        />
      </div>
      <ul class="flex flex-col py-4">
        <li v-for="(tab, index) in tabs" :key="`tab-${index}`">
          <NuxtLink
            :to="tab.route"
            class="flex flex-row items-center h-12 text-gray-500 transition-transform duration-200 ease-in transform hover:translate-x-2 hover:text-gray-800"
          >
            <span
              class="inline-flex items-center justify-center w-12 h-12 text-lg text-gray-400 "
              ><i class="bx bx-home"></i
            ></span>
            <span class="text-sm font-medium">{{ tab.name }}</span>
          </NuxtLink>
        </li>
      </ul>
    </div>
    <div class="flex flex-1 overflow-hidden">
      <div class="flex-1 ml-5 overflow-y-scroll">
        <slot />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data: () => {
    return {
      tabs: [
        {
          route: "/",
          name: "About",
        },
        {
          route: "/projects",
          name: "Projects",
        },
        {
          route: "/skills",
          name: "Skills",
        },
        {
          route: "/interests",
          name: "Interests",
        },
        {
          route: "/blog",
          name: "Blog",
        },
      ],
    };
  },
};
</script>
