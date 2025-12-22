<template>
    <footer class="footer">
        <div class="footer__container">
            
        </div>
    </footer>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
    @use '~/assets/scss/abstracts' as *;

    .footer {
        $p: &;

        &__container {
            @include content-container;
        }
    }
</style>
