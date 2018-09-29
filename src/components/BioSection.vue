<template>
<div class="container biog">    
    <div class="row align-items-center">
        <div class="col-sm-3">
            <img src="../assets/ben.jpg" alt="benjamin vockenberg">
        </div>
        <div class="col-sm-9">            
            <h2>{{ entry.data.title }}</h2>
            <div class="vhtml" v-html="entry.data.content"></div>
        </div>
    </div>        
</div>
</template>

<script>

//Axios as firebase api consumer
import axios from 'axios';

export default {
    name: 'BioSection',
    data() {
        return {
            // Data struct from firebase
            entry : {
                title : null,
                content: null
            }
        }
    },
    mounted() {
        axios.get('https://littleblog-c8a97.firebaseio.com/entry.json').then(response => (this.entry = response));
    }
}
</script>

<style scoped lang="scss">
img {
    width: 100%;
}

p, .vhtml {    
    font-size: 22px !important;
}

.biog {
    background-color: rgba(0,0,0, 0.5);
    padding: 2%;
}
</style>
