<template>
    <header class="header">
        <div class="header__container">
            
        </div>
    </header>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
    @use '~/assets/scss/abstracts' as *;

    .header {
        $p: &;

        position: sticky;
        top: 0;
        z-index: 10;
        width: 100%;
        padding: rem(16) 0;
        &__container {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: lineScale(32, 16, 480, 1440);
            @include content-container;
        }
    }
</style>
