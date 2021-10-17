<template>
  <div>
    <page-header
      title="Interests"
      description="I like to learn about different fields and how their integration would help to create a great solution."
    ></page-header>

    <div  class="flex-grow min-h-screen px-10 py-32 bg-gray-100">
      <div
        class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 md:gap-x-10 xl-grid-cols-6 gap-y-10 gap-x-6"
      >
        <div
          v-for="interest in data"
          :key="`${interest._id}-data`"
          class="container max-w-md mx-auto transition duration-300 rounded-lg shadow-lg hover:shadow-2xl"
        >
          <img
            :src="`${interest.image.url}`"
            :alt="`${interest.image.alternativeText}`"
            class="text-center rounded-t-lg w-half"
            width="200px"
          />
          <div class="p-6">
            <h1
              class="text-xl font-bold text-gray-900 transition duration-200 md:text-1xl hover:text-blue-600"
            >
              {{ interest.image.caption }}
            </h1>
            <p class="my-2 text-gray-700 hover-text-900">
              {{ interest.image.alternativeText }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const { data } = await useFetch(`https://api.mexsonfernandes.com/interests`);
</script>
