<script setup>
import { ref } from 'vue';

let query = ref('');
</script>

<template>
    <div class="input-wrapper">
        <input type="text" autofocus v-model="query"/>
    </div>
</template>

<style lang="scss" scoped>
.input-wrapper {
    width: 100%;
    display: flex;
    margin-bottom: 2rem;

    input {
        width: 100%; 
        display: flex;
        padding: 8px 16px;
        border: none;
        outline: none;
        border-radius: 10px;
    }
}

</style>