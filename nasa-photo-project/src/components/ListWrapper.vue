<script setup>
import { ref } from 'vue';
import LoadingSpinner from './LoadingSpinner.vue';
import ListItem from './ListItem.vue';

let query = ref('');
const isLoading = ref(false);
const searchResults = ref([]);

const performSearch = async () => {
    try {
        isLoading.value = true;
        const response = await fetch(`https://images-api.nasa.gov/search?q=${query.value}`);
        const data = await response.json();

        searchResults.value = data.collection.items;
        isLoading.value = false;
    } catch (error) {
        console.error('Error fetching data:', error);
      }
    };
</script>

<template>
    <div class="input-wrapper">
        <input type="text" autofocus v-model="query"/>
        <button @click="performSearch">Search</button>
    </div>
    <div v-if="isLoading === true">
        <LoadingSpinner></LoadingSpinner>
    </div>
    <div v-else-if="searchResults.length > 0 && isLoading === false" class="list-wrapper">
        <template v-for="result in searchResults" :key="result.id">
            <ListItem :cardInformation="result"></ListItem>
        </template>
    </div>
    <div v-else class="empty-list">
        <h1>Sorry, data could not be found</h1>
    </div>
</template>

<style lang="scss" scoped>
.input-wrapper {
    width: 100%;
    display: flex;
    margin-bottom: 4rem;

    input {
        width: 100%; 
        display: flex;
        padding: 8px 16px;
        border: none;
        outline: none;
        border-radius: 10px 0 0 10px;
        background-color: #c3d8ec;
    }

    button {
        border: none;
        font-weight: 500;
        background-color: #6186aa;
        color: #fff;
        border-radius: 0 10px 10px 0;

        &:hover, &:focus {
            background-color: #72818f;
            color: #fff;
        }
    }
}

.list-wrapper {
    display: flex;
    justify-content: center;
    gap: 2rem;
    flex-wrap: wrap;
}

.empty-list {
    color: #fff;
    text-align: center;
    width: 100%;
}
</style>