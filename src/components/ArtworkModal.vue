<template>
    <div class="modal" @click="$emit('close')">
        <div class="modal-content">
            <div class="modal-body" v-if="artwork">
                <img :src="artwork.image" :alt="artwork.title" />
                <div class="description">
                    <h2>{{ artwork.title }}</h2>
                    <p>{{ artwork.price }}</p>
                    <p>{{ artwork.description }}</p>
                </div>
            </div>
            <div v-else>
                <p>No artwork available.</p>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue';

export default defineComponent({
    props: {
        artwork: {
            type: Object as PropType<{ title: string; image: string; price: string; description: string } | null>,
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
    /* Dark background for the whole screen */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

.modal-content {
    background-color: transparent;
    /* Fully transparent background */
    padding: 20px;
    border-radius: 12px;
    max-width: 600px;
    width: 100%;
    position: relative;
    display: flex;
    flex-direction: column;
    border: none;
    box-shadow: none;
}

.modal-body {
    display: flex;
    flex-direction: column;
    /* Stack image and text vertically */
    align-items: center;
    /* Center content */
    max-width: 100%;
}

.modal-body img {
    max-width: 80%;
    /* Slightly smaller image to avoid it taking up too much space */
    height: auto;
    margin-bottom: 15px;
    /* Space between image and description */
    border-radius: 8px;
    transition: transform 0.3s ease;
}

.modal-body img:hover {
    transform: scale(1.05);
    /* Slight zoom effect */
}

.description {
    text-align: center;
    color: #fff;
    /* White text for contrast on transparent background */
    max-width: 90%;
}

.description h2 {
    margin: 10px 0;
    font-size: 1.25rem;
}

.description p {
    margin: 5px 0;
    font-size: 1rem;
}

/* Mobile adjustments */
@media (max-width: 600px) {
    .modal-content {
        max-width: 90%;
        /* Modal takes 90% of the screen width on mobile */
        padding: 15px;
    }

    .modal-body img {
        max-width: 100%;
        /* Image takes full width on small devices */
        margin-bottom: 10px;
    }

    .description {
        margin: 0 10px;
        /* Add padding on mobile to avoid text touching edges */
    }
}
</style>
