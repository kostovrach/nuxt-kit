<template>
    <NuxtLayout>
        <section class="not-found-hero">
            <div class="not-found-hero__container">
                404
            </div>
        </section>
    </NuxtLayout>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
    @use '~/assets/scss/abstracts' as *;

    .not-found-hero {
        @include content-block($margin: rem(32));
        &__container {
            @include content-container;
        }
    }
</style>
