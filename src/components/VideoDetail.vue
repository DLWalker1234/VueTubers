<template>
    <div v-if="video" class="detailGrid">
        <div class="videoEmbed">
            <iframe id="iframe" width="60%" height="80%" v-bind:src="videoUrl" />
        </div>

        <div class="details">
            <h4 id="title">{{ video.snippet.title }}</h4>
            <p>{{ video.snippet.description }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
        videoUrl() {
            const videoId = this.video.id.videoId;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>

<style scoped>



.videoEmbed {
    display: flex;
    justify-content: center;
    height: 60%;
}

#iframe {
    margin-top: 25px;
}

.details {
    text-align: center;
    margin: 2% 5% 5% 5%;
    border: 2px solid #ddd;
    border-radius: 10px;
    
}

.details:hover {
    background-color: #ccc;
}

#title {
    text-decoration: underline;
    
}

p {
    padding: 1%;
}



</style>

