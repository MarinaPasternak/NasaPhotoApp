<script setup>
import { ref, onMounted } from 'vue';

const componentData = ref({
    bannerURL: '',
    title: '',
    description: ''
});

onMounted(() => {
    const apiKey = process.env.VUE_APP_API_KEY;

    fetch(`https://api.nasa.gov/planetary/apod?api_key=${apiKey}`)
    .then((res) => res.json())
    .then((data) => {
        componentData.value = {
            bannerURL: data.hdurl,
            title: data.title,
            description: data.explanation
        }
    });
});

</script>

<template>
    <div class="welcome-banner">
        <img :src="componentData.bannerURL" :alt="componentData.title"/>
    </div>
    <div class="title">{{ componentData.title }}</div>
    <div class="text">{{ componentData.description }}</div>
</template>

<style lang="scss" scoped>
.welcome-banner {
    width: 100vw;
    height: 100vh;
    position: relative;

    img {
        width: 100vw;
        height: 100vh;
        opacity: 0.8;
    }
}

.title {
    font-size: 32px;
    position: absolute;
    top: 90px;
    left: 0;
    right: 0;
    font-weight: 500;
    color: #fff;
}

.text {
    font-size: 20px;
    position: absolute;
    top: 150px;
    font-weight: 400;
    color: #fff;
    text-align: justify;
    padding: 0 70px;
    letter-spacing: 2px;
}
</style>