<template>
    <div class="works">
        <div class="artworks-section">
            <div v-for="(art, index) in artworks" :key="index" class="artwork" @click="selectArtwork(art)">
                <img :src="art.image" :alt="art.title" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    props: [],
    emits: ['show-artwork'],
    setup(props, { emit }) {
        const artworks = [
            {
                title: 'Mihave een Droom',
                image: 'https://images.bellowswang.com/001_mihave_een_droom.jpeg',
                price: '€200',
                description: 'Description of artwork 1'
            },
            {
                title: 'Pablo Suze',
                image: 'https://images.bellowswang.com/002_Pablos_Suze.jpeg',
                price: 'Not available',
                description: 'Description of artwork 2'
            },
            {
                title: 'Schaap',
                image: 'https://images.bellowswang.com/003_schaap.jpg',
                price: 'Not available',
                description: 'Description of artwork 3'
            },
            {
                title: 'Pierogi and Sushi',
                image: 'https://images.bellowswang.com/004_Pierogi_and_Sushi.jpg',
                price: 'Not available',
                description: 'Description of artwork 4'
            }
        ];

        const selectArtwork = (art: any) => {
            emit('show-artwork', art);
        };

        return { artworks, selectArtwork };
    }
});
</script>

<style scoped>
.works {
    display: flex;
    justify-content: center;
    /* Center the entire works section */
    padding: 20px;
}

.artworks-section {
    margin-top: 20px;
    padding: 50px 0;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    /* Change to 2 columns */
    gap: 50px;
    /* Space between items */
    justify-items: center;
    /* Center items in each grid cell */
}

.artwork {
    text-align: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.2s;
    cursor: pointer;
    width: 300px;
    /* Fixed width for the artwork */
    aspect-ratio: 1 / 1;
    /* Keep the artwork square */
    overflow: hidden;
    /* Hide overflow to crop images */
}

.artwork img {
    width: 100%;
    /* Make image take full width of the container */
    height: 100%;
    /* Ensure the image takes full height */
    object-fit: cover;
    /* Maintain aspect ratio while covering */
    border-radius: 5px;
    /* Add some border radius */
}

@media (max-width: 768px) {
    .artworks-section {
        grid-template-columns: 1fr;
        /* One column on smaller screens */
    }
}
</style>
