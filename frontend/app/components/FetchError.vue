<template>
    <div class="fetch-error">
        <p class="fetch-error__title">Не удалось загрузить</p>
        <button class="fetch-error__button" @click="refreshPage">
            <span>Попробовать снова ↺</span>
        </button>
    </div>
</template>

<script setup lang="ts">
    function refreshPage() {
        refreshNuxtData();
    }
</script>

<style scoped lang="scss">
    @use '~/assets/scss/abstracts' as *;

    .fetch-error {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>
