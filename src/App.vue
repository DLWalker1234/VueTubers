<template>
    <div class="main">
        <SearchBar class="SearchBar" v-on:newSearch="onNewSearch"></SearchBar>
        <VideoDetail v-bind:video="selectedVideo" class="VideoDetail" ></VideoDetail>
        <VideoList class="VideoList" v-on:videoSelect="onVideoSelect" v-bind:videos="videos" ></VideoList>
    </div>
</template>

<script> 

import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY = 'AIzaSyDlBEi0I4BRiANflvUnCKHbr9khDO6cOqk';

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetail
        
    },
    data: function() {
        return {
            videos: [],
            selectedVideo: null
        };
    },
    methods: {
        onNewSearch: function(newSearch) {
            console.log(newSearch);
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: newSearch

                }
            }).then(response => {
                console.log(response.data.items);
                this.videos = response.data.items;
            });
        },
        onVideoSelect: function(video) {
            this.selectedVideo = video;
        }
    }
};
</script>

<style lang="scss" scoped>
  @import 'main.scss'
</style>
