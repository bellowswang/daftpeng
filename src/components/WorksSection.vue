<template>
    <div :class="worksClass">
        <div :class="artworksGridClass">
            <div v-for="(art, index) in artworks" :key="index" class="artwork" @click="selectArtwork(art)">
                <img :src="art.image" :alt="art.title" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, toRefs, computed } from 'vue';

export default defineComponent({
    props: {
        isSmallGrid: {
            type: Boolean,
            required: true
        }
    },
    emits: ['show-artwork'],
    setup(props, { emit }) {
        const { isSmallGrid } = toRefs(props);

        const artworks = [
            {
                title: 'Hi Have Een Droom',
                image: 'https://images.bellowswang.com/001_mihave_een_droom.jpeg',
                price: '€200',
                description: 'Inspired by the best-known street poems in Rotterdam.'
            },
            {
                title: 'Pablo\'s Suze',
                image: 'https://images.bellowswang.com/002_Pablos_Suze.jpeg',
                price: 'Not available',
                description: 'Loving the color and the texture Picasso chose in Glass and bottle of Suze.'
            },
            {
                title: 'Schaap',
                image: 'https://images.bellowswang.com/003_schaap.jpg',
                price: 'Not available',
                description: 'Sheep is me, me as a sheep.'
            },
            {
                title: 'Pierogi and Sushi',
                image: 'https://images.bellowswang.com/004_Pierogi_and_Sushi.jpg',
                price: 'Not available',
                description: 'To a lovely couple.'
            }
        ];

        const selectArtwork = (art: any) => {
            emit('show-artwork', art);
        };

        const artworksGridClass = computed(() => {
            return isSmallGrid.value ? 'artworks-section-small' : 'artworks-section';
        });

        const worksClass = computed(() => {
            return isSmallGrid.value ? 'works-small' : 'works';
        });

        return { artworks, selectArtwork, artworksGridClass, worksClass };
    }
});
</script>

<style scoped>
.works {
    display: flex;
    justify-content: center;
    /* Center in normal view */
    padding: 20px;
}

.works-small {
    display: flex;
    /* Maintain flex layout */
    padding: 20px;
    width: 50%;
    transform: translateX(50%);
    /* Padding for small grid view */
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
    text-align: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.2s;
    cursor: pointer;
    width: 300px;
    aspect-ratio: 1 / 1;
    overflow: hidden;
}

.artworks-section-small .artwork {
    width: 150px;
    aspect-ratio: 1 / 1;
}

.artwork img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

@media (max-width: 768px) {
    .artworks-section {
        grid-template-columns: 1fr;
    }
}

@media (max-width: 1200px) {
    .artworks-section-small {
        grid-template-columns: repeat(2, 1fr);
        /* 2 artworks per row on medium screens */
    }
}

@media (max-width: 768px) {
    .artworks-section-small {
        grid-template-columns: repeat(1, 1fr);
        /* 1 artworks per row on smaller screens */
    }
}
</style>