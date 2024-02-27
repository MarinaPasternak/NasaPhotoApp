<script setup>
import {ref, defineProps } from 'vue';

const props = defineProps(['cardInformation', 'cardImgURL']);

const cardData = ref(props.cardInformation);
const cardImgURL = ref(props.cardImgURL);

</script>

<template>
    <div class="card">
        <img :src="cardImgURL" :alt="cardData.center">
        <div class="container">
            <h3>{{ cardData.center }}</h3>
            <p>{{ cardData.description }}</p>
            <div class="badges-list">
                <div v-for="keyword in cardData.keywords" :key="keyword">
                    {{ keyword }}
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>

.card {
    background-color: #c3d8ec;
    width: 400px;
    height: 450px;
    padding: 30px 20px 20px 20px;

    &:hover {
        transform: scale(1.1);
    }

    img {
        max-width: 390px;
        max-height: 200px;
    }

    h3 {
        color: #2c3e50;
    }

    p {
        display: -webkit-box;
        -webkit-box-orient: vertical;
        overflow: hidden;
        -webkit-line-clamp: 5;
        text-align: justify;
    }

    .badges-list {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 5px;
        flex-wrap: wrap;
        
        div {
            border-radius: 15px;
            background-color: #155e6a;
            color: #fff;
            text-align: center;
            padding: 10px;
        }
    }
}
</style>