<script setup>
const props = defineProps({
  artists: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <div class="bg-gray-900 text-white min-h-screen py-8">
    <h2 class="text-4xl font-semibold text-center mb-8">Artistes</h2>

    <div
      class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 px-6"
    >
      <div
        v-for="artist in props.artists"
        :key="artist.id"
        class="bg-gray-800 rounded-lg overflow-hidden shadow-xl transform hover:scale-105 transition duration-300 ease-in-out"
      >
        <!-- Image de l'artiste -->
        <div class="relative">
          <img
            :src="artist.songs[0].image"
            class="w-full h-48 object-cover rounded-t-lg"
          />
        </div>

        <div class="p-4">
          <!-- Nom de l'artiste -->
          <h3 class="text-2xl font-semibold text-center mb-4">
            {{ artist.artist }}
          </h3>

          <ul class="space-y-4">
            <!-- Afficher les chansons de chaque artiste -->
            <li
              v-for="song in artist.songs"
              :key="song.id"
              class="flex items-center justify-between"
            >
              <div class="flex items-center space-x-3">
                <img
                  :src="song.image"
                  class="w-12 h-12 object-cover rounded-full"
                />
                <h4 class="text-lg font-medium text-gray-200">
                  {{ song.title }}
                </h4>
              </div>
              <!-- Bouton play -->
              <audio
                :src="song.music"
                controls
                class="w-20 h-10 text-gray-500"
              ></audio>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
