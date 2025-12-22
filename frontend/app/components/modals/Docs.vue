<template>
    <VueFinalModal
        overlay-transition="vfm-fade"
        content-transition="vfm-slide-right"
        swipe-to-close="right"
    >
        <div class="modal-privacy">
            <div class="modal-privacy__container">
                <button class="modal-privacy__button" type="button" @click="emit('close')">
                    <SvgSprite type="cross" :size="32" />
                </button>
                <div class="modal-privacy__titlebox">
                    <h1 class="modal-privacy__title">{{ props.title }}</h1>
                    <span v-if="props.dateUpdated" class="modal-privacy__tag">
                        Последнее обновление: {{ normalizeDate(props.dateUpdated) }}
                    </span>
                </div>
                <div class="modal-privacy__body">
                    <div
                        v-show="status === 'idle' || status === 'pending'"
                        class="modal-privacy__loader"
                    >
                        <TextModalLoader />
                    </div>
                    <div v-show="status === 'error'" class="modal-privacy__error">
                        <FetchError />
                    </div>
                    <div
                        v-show="status === 'success'"
                        class="modal-privacy__content"
                        v-html="props.content"
                    ></div>
                </div>
            </div>
        </div>
    </VueFinalModal>
</template>

<script setup lang="ts">
    import type { AsyncDataRequestStatus } from '#app';
    import { VueFinalModal } from 'vue-final-modal';

    const props = withDefaults(
        defineProps<{
            title: string;
            dateUpdated: string;
            content: string;
            status: AsyncDataRequestStatus;
        }>(),
        {
            title: '',
            dateUpdated: '',
            content: '',
            status: 'idle',
        }
    );

    const status = computed(() => props.status);

    const emit = defineEmits<{
        (e: 'close'): void;
    }>();
</script>

<style lang="scss">
    @use '~/assets/scss/abstracts' as *;

    .modal-privacy {
        $p: &;

        position: absolute;
        top: 0;
        right: 0;
        width: 100%;
        max-width: rem(754);
        height: 100lvh;
        overflow-y: auto;
        color: $c-FFFFFF;
        // background-color: $c-secondary;
        @include hide-scrollbar;
        &__container {
            display: flex;
            flex-direction: column;
            padding: rem(32);
        }
        &__button {
            align-self: flex-end;
        }
        &__titlebox {
            display: flex;
            flex-direction: column;
            gap: rem(32);
            margin-top: rem(16);
        }
        &__title {
            font-size: lineScale(48, 24, 480, 1440);
            font-weight: $fw-semi;
        }
        &__tag {
            font-size: lineScale(16, 14, 480, 1440);
            color: $c-accent;
        }
        &__body {
            margin-top: rem(64);
        }
        &__content {
            display: flex;
            flex-direction: column;
            h2 {
                text-transform: uppercase;
                font-size: lineScale(24, 18, 480, 1440);
                // font-weight: $fw-semi;
                margin: rem(32) 0 rem(8);
            }
            h3,
            h4,
            h5,
            h6 {
                font-size: rem(16);
                // font-weight: $fw-bold;
                margin: rem(24) 0 rem(8);
            }

            p {
                font-size: rem(14);
                line-height: 1.3;
                margin: rem(16) 0 rem(8);
                > a {
                    color: $c-accent;
                    text-decoration: underline;
                    @media (pointer: fine) {
                        &:hover {
                            text-decoration: none;
                        }
                    }
                }
            }
        }
    }
</style>
