<template>
    <div class="root" v-on:click="onYouTubeIframeAPIReady">
        <iframe id="player"
            width="100%"
            height="100%"
            :src="'https://www.youtube.com/embed/' + getID + '?autoplay=1'"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
        ></iframe>
    </div>
</template>

<script>
export default {
    components: {},
    data() {
        return {
            value: 0,
            url: "https://www.youtube.com/embed/",
        };
    },
    methods: {},
    computed: {
        getID() {
            return this.$store.state.playlists.currentSong;
        },
    },
};
</script>

<style scoped>
.root {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.root > div {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    height: 50%;
    width: 100%;
}

input {
    width: 3vw;
    height: 3vh;
}

#player {
    width: 100vw;
    height: 100vh;
}

@media screen and (max-width: 1024px) {
}

@media screen and (max-width: 375px) {
    input {
        width: 10vw;
        height: 5vh;
    }
}
</style>
