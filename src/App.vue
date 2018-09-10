<template>
<div id="app">    
    <info-section />
    <Countdown />
    <br><br>
    <BioSection />
</div>
</template>

<script>

import Countdown from './components/Countdown.vue';
import BioSection from './components/BioSection.vue';
import InfoSection from './components/InfoSection.vue';

export default {
    name: 'app',
    components: { Countdown, BioSection, InfoSection }
}
</script>

<style lang="scss">

@import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
@import url('https://fonts.googleapis.com/css?family=Exo:100');
@import url('https://fonts.googleapis.com/css?family=Oswald:600');

body {
    background: url('assets/starry_sky_galaxy_universe_sky_night_118591_1920x1080.jpg') 50% 0 no-repeat fixed;
    background-size: cover;
}

#app {
    font-family: sans-serif;
    margin-top: 60px;

    h1, h2, h3, h4, h5, h6, p {
        color: whitesmoke;
    }
}
</style>
