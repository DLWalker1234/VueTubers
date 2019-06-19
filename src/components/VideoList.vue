<template>
    <ul class="VList">
       <VideoListItem 
            v-for="video in videos"
            v-bind:video="video"
            :key="video.etag"
            @videoSelect="onVideoSelect"
        >
       </VideoListItem>
    </ul>


</template>

<script>

import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videos: Array
    },
    methods: {
      onVideoSelect(video) {
          this.$emit('videoSelect', video);
      }  
    }
}

</script>
    

<style>

.VList {
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
}
 

ul {
    list-style-type: none;
}

</style>
