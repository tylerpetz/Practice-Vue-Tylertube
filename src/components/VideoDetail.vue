<template>
    <div class="modal" :class="{ 'is-active': modal }">
        <div class="modal-background" @click="closeModal"></div>
        <div class="modal-content" v-if="video">
            <p class="image is-16by9">
                <iframe
                :src="videoUrl"
                />
            </p>
        </div>
        <button class="modal-close is-large" aria-label="close" @click="closeModal"></button>
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video', 'modal'],
    computed: {
        videoUrl() {
            const { videoId } = this.video.id;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    },
    methods: {
        closeModal() {
            this.$emit('modalClose', false);
        }
    }
};
</script>

<style scoped>
.image iframe {
    display: block;
    height: auto;
    width: 100%;
    height: 100%;
    bottom: 0;
    left: 0;
    position: absolute;
    right: 0;
    top: 0
}

.fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
}

.fade-enter, .fade-leave-to {
    opacity: 0;
}
</style>