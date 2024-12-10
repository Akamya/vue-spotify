<script setup>
import MusicCard from "../components/MusicCard.vue";
import { ref, onMounted } from "vue";

const artists = ref([]); // Déclare une variable réactive pour les données

// Charger les données JSON depuis un fichier local
onMounted(async () => {
  try {
    const response = await fetch("./data.json");
    const data = await response.json();
    artists.value = data.artists; // Mettre à jour la variable réactive
  } catch (error) {
    console.error("Erreur lors du chargement des données JSON :", error);
  }
});
</script>

<template>
  <MusicCard :artists="artists"></MusicCard>
</template>
