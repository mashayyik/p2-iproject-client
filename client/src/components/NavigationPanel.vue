<script>
import { useAuctionStore } from "../stores/auction.js";
import { mapActions, mapState } from "pinia";
export default {
  data() {
    return {
      filter: {
        search: "",
        category: "",
      },
    };
  },
  methods: {
    ...mapActions(useAuctionStore, ["fetchAllAuction"]),
    handleSearch() {
      this.fetchAllAuction(this.filter);
    },
  },
};
</script>

<template>
  <div class="w-[60%] mx-auto mt-10 bg-slate-300 p-3 m-2 rounded-xl">
    <div class="flex gap-2 justify-center">
      <div>
        <div class="relative w-full">
          <div
            class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none"
          >
            <svg
              aria-hidden="true"
              class="w-5 h-5 text-gray-500 dark:text-gray-400"
              fill="currentColor"
              viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                clip-rule="evenodd"
              ></path>
            </svg>
          </div>
          <input
            type="text"
            v-model="filter.search"
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            placeholder="ex: nasi padang "
          />
        </div>
      </div>
      <div>
        <select
          v-model="filter.category"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        >
          <option value="">Choose a Category</option>
          <option value="power_supply">Power Supply</option>
          <option value="ram">RAM</option>
          <option value="cpu_fan">CPU Fan</option>
          <option value="case">Case</option>
          <option value="storage">Storage</option>
          <option value="mouse">Mouse</option>
          <option value="keyboard">Keyboards</option>
          <option value="processor">Processsors</option>
          <option value="gpu">GPU</option>
        </select>
      </div>
      <button
        @click.prevent="handleSearch"
        class="p-2.5 ml-2 flex justify-center items-center text-sm font-medium text-white bg-blue-700 rounded-lg border border-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
      >
        <svg
          class="w-5 h-3"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
          ></path>
        </svg>
        <span class="">Search</span>
      </button>
    </div>
  </div>
</template>
