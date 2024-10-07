<template>
    <div class="header">
        <div class="left">
            <h1>Daftpeng</h1>
        </div>
        <div class="right">
            <a @click="scrollToSection('works')">Works</a>
            <a @click="scrollToSection('about')">About</a>
        </div>
    </div>
</template>

<script lang="ts">
export default {
    methods: {
        scrollToSection(section: string) {
            const sectionEl = document.getElementById(`${section}-section`);
            sectionEl?.scrollIntoView({ behavior: 'smooth' });
        }
    }
};
</script>

<style scoped>
.header {
    position: fixed;
    /* Keeps the banner fixed at the top */
    display: flex;
    /* Enable flexbox layout */
    justify-content: space-between;
    /* Space between left and right */
    align-items: center;
    /* Center items vertically */
    padding: 20px;
    background-color: #f8f8f8;
    /* Light grey background for the header */
    width: 100%;
    /* Ensure the header spans the full width */
    z-index: 1000;
    /* Ensure it stays on top of other elements */
}

.left {
    flex: 1;
    /* Allows the left section to take up space */
}

.left h1 {
    font-size: 24px;
    /* Title font size */
    margin: 0;
    /* Remove default margin */
}

.right {
    display: flex;
    /* Align links horizontally */
}

.right a {
    margin-left: 20px;
    /* Space between links */
    cursor: pointer;
    /* Change cursor to pointer on hover */
}
</style>
