<template>
    <div :class="worksClass">
        <div :class="artworksGridClass">
            <div v-for="(art, index) in artworks" :key="index" class="artwork" @click="selectArtwork(art)">
                <img :src="art.image" :alt="art.title" />
                <div class="artwork-title">{{ art.title }}</div>
            </div>
        </div>
        <div v-if="selectedArtwork" class="artwork-modal" @click="closeModal">
            <div class="artwork-modal-content">
                <img :src="selectedArtwork.image" :alt="selectedArtwork.title" />
                <div class="artwork-modal-text">
                    <h2>{{ selectedArtwork.title }}</h2>
                    <p>{{ selectedArtwork.description }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, toRefs, computed, ref } from 'vue';

export default defineComponent({
    props: {
        isSmallGrid: {
            type: Boolean,
            required: true
        }
    },
    setup(props) {
        const { isSmallGrid } = toRefs(props);
        const selectedArtwork = ref(null);

        const artworks = [
            {
                title: 'Mi Have Een Droom',
                image: 'https://images.bellowswang.com/001_mihave_een_droom.jpeg',
                description: 'Inspired by the best-known street poems in Rotterdam.'
            },
            {
                title: 'Pablo\'s Suze',
                image: 'https://images.bellowswang.com/002_Pablos_Suze.jpeg',
                description: 'Loving the color and the texture Picasso chose in Glass and bottle of Suze.'
            },
            {
                title: 'Schaap',
                image: 'https://images.bellowswang.com/003_schaap.jpg',
                description: 'Sheep is me, me as a sheep.'
            },
            {
                title: 'Pierogi and Sushi',
                image: 'https://images.bellowswang.com/004_Pierogi_and_Sushi.jpg',
                description: 'To a lovely couple.'
            }
        ];

        const selectArtwork = (art: any) => {
            selectedArtwork.value = art;
        };

        const closeModal = () => {
            selectedArtwork.value = null;
        };

        const artworksGridClass = computed(() => {
            return isSmallGrid.value ? 'artworks-section-small' : 'artworks-section';
        });

        const worksClass = computed(() => {
            return isSmallGrid.value ? 'works-small' : 'works';
        });

        return { artworks, selectArtwork, closeModal, selectedArtwork, artworksGridClass, worksClass };
    }
});
</script>

<style scoped>
.works {
    display: flex;
    justify-content: center;
    padding: 0px;
}

.works-small {
    display: flex;
    padding: 20px;
    width: 50%;
    transform: translateX(50%);
}

.artworks-section {
    margin-top: 50px;
    padding: 50px 0;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 50px;
    justify-items: center;
}

.artworks-section-small {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 50px;
    justify-items: center;
}

.artwork {
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.2s;
    cursor: pointer;
    width: 300px;
    aspect-ratio: 1 / 1;
    overflow: hidden;
    display: flex;
    flex-direction: column;
}

.artworks-section-small .artwork {
    width: 150px;
    aspect-ratio: 1 / 1;
}

.artwork img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    flex-grow: 1;
}

.artwork-title {
    padding: 10px;
    text-align: center;
    background-color: #fff;
}

.artwork-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

.artwork-modal-content {
    background-color: #fff;
    padding: 20px;
    border-radius: 0px;
    max-width: 80%;
    max-height: 80%;
    overflow: auto;
}

.artwork-modal-content img {
    max-width: 100%;
    height: auto;
}

.artwork-modal-text {
    margin-top: 20px;
}

.artwork-modal-text h2 {
    margin: 0;
}

.artwork-modal-text p {
    margin: 10px 0 0;
}

@media (max-width: 768px) {
    .artworks-section {
        grid-template-columns: 1fr;
    }
}

@media (max-width: 1200px) {
    .artworks-section-small {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 768px) {
    .artworks-section-small {
        grid-template-columns: repeat(1, 1fr);
    }
}
</style>