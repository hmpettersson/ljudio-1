<template>
    <div class="main">
        <div id="row">
            <div class="left">
                <Playlists class="playlists" user="User" />
                <NavBar class="navbar" />
            </div>
            <div class="right">
                <div class="top">
                    <PlaylistHeader
                        class="playlist-header"
                        playlistName="My Playlist"
                    />
                    <SearchField class="search-field" />
                </div>
                <PlaylistContent class="playlist-content" />
                <SlidingSideNav class="sliding-side-nav" />
            </div>
        </div>
        <Timeline class="timeline" />
        <Popup v-if="checkPopupState"/>
    </div>
</template>

<script>
import Playlists from "../components/Playlists.vue";
import PlaylistHeader from "../components/PlaylistHeader.vue";
import PlaylistContent from "../components/PlaylistContent.vue";
import Timeline from "../components/Timeline.vue";
import SearchField from "../components/SearchField.vue";
import NavBar from "../components/NavBar.vue";
import SlidingSideNav from "../components/SlidingSideNav.vue";
import Popup from "../components/Popup.vue"

export default {
    name: "App",
    components: {
        Playlists,
        PlaylistHeader,
        PlaylistContent,
        Timeline,
        SearchField,
        NavBar,
        SlidingSideNav,
        Popup
    },
    computed: {
        checkPopupState() {
            console.log(this.$store.state.playlists.showPlaylistPopup);
            return this.$store.state.playlists.showPlaylistPopup;
        },
        getPlaylists() {
            return this.$store.state.playlists.userPlaylistsIDs;
        },
    },
};
</script>

<style scoped>
.main {
    display: flex;
    flex-direction: column;
}

.row {
    display: flex;
    flex-direction: row;
}

.left {
    display: flex;
    flex-direction: column;
    width: 15vw;
    height: 100vh;
    justify-content: space-evenly;
    border-right: 1px solid #323232;
}

.right {
    display: flex;
    flex-direction: column;
    width: 83vw;
}

.playlists {
    height: 90vh;
    overflow: auto;
    overflow-x: hidden;
}

.navbar {
    height: 10vh;
}

.sliding-side-nav {
    display: block;
}

.top {
    display: flex;
    flex-direction: row;
    border-bottom: 1px solid #323232;
}

.playlist-header {
    height: 15vh;
    width: 70%;
    overflow: hidden;
}

.search-field {
    height: 15vh;
    width: 30%;
}

.playlist-content {
    height: 85vh;
    width: 100%;
    overflow: auto;
}

.timeline {
}

.songitem {
    height: 55vh;
}

@media screen and (max-width: 1024px) {
    .playlist-header {
        height: 15vh;
        width: 50%;
    }

    .search-field {
        height: 15vh;
        width: 50%;
    }
}

@media screen and (max-width: 600px) {
    .left {
        display: none;
    }

    .right {
        width: 100vw;
    }

    .top {
        display: flex;
        flex-direction: column;
    }

    .playlist-header {
        display: flex;
        height: 50%;
        width: 100%;
        align-items: center;
    }

    .search-field {
        display: flex;
        height: 15vh;
        width: 100%;
        align-items: flex-end;
    }

    .timeline {
        position: fixed;
        bottom: 0;
        width: 100%;
        background-color: #ffffff;
    }

    .sliding-side-nav {
        display: block;
        position: fixed;
        bottom: 0;
        width: 100%;
    }
}
</style>
