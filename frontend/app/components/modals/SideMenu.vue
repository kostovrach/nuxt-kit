<template>
    <VueFinalModal
        overlay-transition="vfm-fade"
        content-transition="vfm-slide-right"
        swipe-to-close="right"
    >
        <div class="menu">
            <div class="menu__container">
                <div class="menu__header">
                    <button class="menu__button" type="button" @click="emit('close')">
                        <SvgSprite type="cross" :size="32" />
                    </button>
                </div>

                <nav class="menu__nav">
                    <NuxtLink
                        :class="[
                            'menu__nav-link',
                            route.name === 'index' ? 'menu__nav-link--current' : '',
                        ]"
                        :to="{ name: 'index' }"
                    >
                        <span>Главная</span>
                    </NuxtLink>
                </nav>
            </div>
        </div>
    </VueFinalModal>
</template>

<script setup lang="ts">
    import { VueFinalModal } from 'vue-final-modal';
    import { useModal } from 'vue-final-modal';

    const emit = defineEmits<{
        (e: 'close'): void;
    }>();

    const route = useRoute();
</script>

<style scoped lang="scss">
    @use '~/assets/scss/abstracts' as *;

    .menu {
        $p: &;
        $px: rem(32);

        position: absolute;
        top: 0;
        right: 0;
        width: 100%;
        max-width: rem(540);
        height: 100vh;
        color: $c-FFFFFF;
        background-color: $c-secondary;
        &__container {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: $px 0;
        }
        &__header {
            width: 100%;
            display: flex;
            flex-direction: column;
            padding: 0 $px;
        }
        &__button {
            align-self: flex-end;
        }
    }
</style>
