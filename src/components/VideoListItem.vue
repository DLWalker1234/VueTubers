<template>
    <li class="item" @click="onVideoSelect">
        <img v-bind:src="thumbnailUrl" />
        <p class="listTitle">{{ video.snippet.title }}</p>
    </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['video'],
    
    computed: {
        thumbnailUrl() {
            return this.video.snippet.thumbnails.default.url;
        }
    },
    methods: {
        onVideoSelect() {
            this.$emit('videoSelect', this.video);
        }
    }
};
</script>

<style>

.item {
    border: 2px solid #ccc;
    border-radius: 5px;
    display: flex;    
}

.item:hover {
    background-color: #ccc;
}

.listTitle {
    display: flex;
    justify-content: center;
    padding-left: 10px;
}

</style>
