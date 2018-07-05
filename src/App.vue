<template>
    <div>
        <section class="hero is-dark is-bold">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">tyler<span>Tube</span></h1>
                </div>
            </div>
        </section>
        <SearchBar 
        @termChange="onTermChange"
        />
        <VideoList 
        :videos="videos"
        @videoSelect="onVideoSelect" 
        />
        <VideoDetail :video="selectedVideo" :modal="showModal" @modalClose="closeModal" />
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
const API_KEY = 'AIzaSyBbi2nJH-DSvbqgCw7rHZUKo_G4m3P97RI';

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetail
    },
    data() {
        return {
            videos: [],
            selectedVideo: null,
            showModal: false,
        };
    },
    methods: {
        onVideoSelect(video) {
            this.selectedVideo = video;
            this.showModal = true;
        },
        closeModal() {
            this.showModal = false;
        },
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', 
            {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items;
            })
        }
    }
};
</script>

<style>
body {
    padding-bottom: 100px;
}
</style>

<style scoped>
h1 {
    text-align: center;
}

h1 span {
    display: inline-block;
    color: white;
    background-color: red;
    padding: 3px;
    margin-left: 8px;
    border-radius: 10px;
}

.hero {
    margin-bottom: 40px;
}
</style>