<template>
    <div class="header">
        <div class="left">
            <h1>Daftpeng/peng</h1>
        </div>
        <div class="right">
            <a @click="navigate('works')">Works</a>
            <a @click="navigate('about')">About</a>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    setup(props, { emit }) {
        const navigate = (section: string) => {
            emit('navigate', section);
        };

        return { navigate };
    }
});
</script>

<style scoped>
.header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px 300px;
    background-color: #ffffff;
    z-index: 1000;
    /* Ensure the header stays on top */
    /* Optional shadow for a floating effect */
}

.left {
    flex: 0.5;
}

.left h1 {
    font-size: 24px;
}

.right {
    display: flex;
}

.right a {
    margin-left: 15px;
    cursor: pointer;
}

/* Media query for mobile screens */
@media (max-width: 768px) {
    .header {
        padding: 20px 20px;
        /* Adjust padding for smaller screens */
    }

    .left h1 {
        font-size: 18px;
        /* Optional: Adjust font size for mobile */
    }

    .right a {
        margin-left: 10px;
        /* Optional: Adjust margin for mobile */
    }
}
</style>