<template>
  <div class="border-2 border-gray-200 rounded m-4 p-4">
    <h2 class="text-3xl font-bold mb-2">
      Old World
    </h2>
    <div v-for="(island, index) in islands" class="border-t-2 border-gray-200">
      <div class="mt-2">
        <h3 class="text-2xl font-bold inline-block">
          {{island}}
        </h3>
        <button
            @click="deleteIsland(index)"
            type="button"
            class="float-right focus:outline-none text-black bg-yellow-400 hover:bg-yellow-500 focus:ring-4 focus:ring-yellow-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2"
        >
          Delete
        </button>
      </div>
      <IslandOldWorld></IslandOldWorld>
    </div>
    <div class="border-t-2 border-gray-200">
      <input
          type="text"
          v-model="name"
          class="mr-2 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 w-56 p-2.5"
      >
      <button
          @click="addIsland()"
          type="button"
          class="mt-4 focus:outline-none text-black bg-yellow-400 hover:bg-yellow-500 focus:ring-4 focus:ring-yellow-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2"
      >
        Add Island
      </button>
    </div>
  </div>
</template>

<script>
import IslandOldWorld from "@/components/IslandOldWorld.vue";

export default {
  components: {IslandOldWorld},
  data() {
    return {
      name: '',
      islands: [],
    }
  },
  methods: {
    addIsland() {
      this.islands.push(this.name);
      this.name = '';
    },
    deleteIsland(index) {
      this.islands.splice(index, 1);
    }
  }
};
</script>