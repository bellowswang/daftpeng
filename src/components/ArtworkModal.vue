<template>
    <div class="modal">
        <div class="modal-content">
            <span class="close-btn" @click="$emit('close')">&times;</span>
            <div class="modal-body" v-if="artwork"> <!-- Ensure artwork is not null before rendering -->
                <img :src="artwork.image" :alt="artwork.title" />
                <div class="description">
                    <h2>{{ artwork.title }}</h2>
                    <p>{{ artwork.price }}</p>
                    <p>{{ artwork.description }}</p>
                </div>
            </div>
            <div v-else>
                <p>No artwork available.</p> <!-- Message for null artwork -->
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue';

export default defineComponent({
    props: {
        artwork: {
            type: Object as PropType<{ title: string; image: string; price: string; description: string } | null>, // Allow null
            required: true
        }
    }
});
</script>

<style scoped>
/* Modal Styling */
.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7);
    /* Dark semi-transparent background */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

.modal-content {
    background-color: white;
    padding: 20px;
    border-radius: 8px;
    max-width: 90%;
    width: 100%;
    position: relative;
    display: flex;
    flex-direction: column;
}

.close-btn {
    position: absolute;
    top: 10px;
    right: 20px;
    font-size: 24px;
    cursor: pointer;
}

.modal-body {
    max-width: 100%;
    display: flex;
}

.modal-body img {
    max-width: 400px;
    height: auto;
    margin-right: 20px;
}

.description {
    flex: 1;
    /* Allow the description to take the remaining space */
}
</style>
