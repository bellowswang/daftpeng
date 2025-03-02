<template>
  <div id="app">
    <!-- Header -->
    <AppHeader @navigate="handleNavigation" />

    <!-- Main Content -->
    <div v-if="activeSection === 'works'">
      <Works :isSmallGrid="false" @show-artwork="showArtwork" />
    </div>
    <div v-if="activeSection === 'about'">
      <About />
      <Works :isSmallGrid="true" @show-artwork="showArtwork" />
    </div>

    <!-- Artwork Modal -->
    <ArtworkModal v-if="showModal" :artwork="selectedArtwork" @close="closeModal" />
  </div>
</template>

<script lang="ts">
import { ref } from 'vue';
import AppHeader from './components/HeaderSection.vue';
import Works from './components/WorksSection.vue';
import About from './components/AboutSection.vue';
import ArtworkModal from './components/ArtworkModal.vue';

export default {
  components: {
    AppHeader,
    Works,
    About,
    ArtworkModal
  },
  setup() {
    const showModal = ref(false);
    const selectedArtwork = ref(null);
    const activeSection = ref('works'); // Default to showing the works section

    const showArtwork = (artwork: any) => {
      selectedArtwork.value = artwork;
      showModal.value = true;
    };

    const closeModal = () => {
      showModal.value = false;
    };

    const handleNavigation = (section: string) => {
      activeSection.value = section; // Switch between 'works' and 'about'
    };

    return { showModal, selectedArtwork, showArtwork, closeModal, activeSection, handleNavigation };
  }
};
</script>


<style>
@import './assets/main.css';
/* Importing the global styles */
</style>
