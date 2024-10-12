<template>
    <div class="header">
        <div class="header-content">
            <div class="left">
                <h1 @click="navigate('works')" class="clickable-title">Daftpeng/peng</h1>
            </div>
            <div class="right">
                <a @click="navigate('works')">Works</a>
                <a @click="navigate('about')">About</a>
            </div>
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
    padding: 20px;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #ffffff;
    z-index: 1000;
    /* Ensure the header stays on top */
    /* Optional shadow for a floating effect */
}


.header-content {
    width: 50%;
    /* Restrict the content width to 50% */
    display: flex;
    justify-content: space-between;
    /* Ensure elements within the content are spaced evenly */
    align-items: center;
    transform: translateX(50%);
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

.clickable-title {
    cursor: pointer;
    /* Optional: to indicate it's clickable */
}
</style>