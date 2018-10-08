<template>
<div>
    <div class="container">    
        <div class="row biog">
            <div class="col-sm-3">
                <img src="../assets/ben.jpg" alt="benjamin vockenberg">
            </div>

            <div class="col-sm-9">            
                <h2>I'll be back...</h2>
                <p>...after spending some time with my daughter. Thank you <strong>Reservix GmbH</strong> for giving me the chance to take a parental leave of 4 month.</p>
                <p><strong>Special thx to:</strong> Helge Hollander, Katrin Stahlberg, Johannes Tolle, Katharina Junker, Benjamin Berg &amp; Carsten Müller</p>
                <p><strong>Thx to the team:</strong> Julia, Lea, Yook, Christian, Rafi, Ewgenij, Alexey, Andres, Dome, Matthias, Wiktor &amp; to all the other colleagues I missed!</p>
                <p>Best whishes Ben, Anne-Katrin &amp; Hannah-Marie</p>
            </div>
        </div>  
    </div>      

    <div class="container">
        <div class="row justify-content-md-center" v-for="(things, index) in reversedData" v-bind:key="index">
            <div class="col-sm-6 achievement">
                <h2>{{ things.title }}</h2>                    
                <h5>{{ things.date}}</h5>
                <p class="vhtml" v-html="things.content"></p>                
            </div>        
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
            entry : { data : [] }
        }
    },
    computed: {
        /**
         * @name fun
         * @returns [Array]
         * @description reverts the array of content to sho latest first 
         */
        reversedData() {
            if (this.entry.data) {
                return (this.entry.data.slice().reverse());
            }
        }
    },    
    mounted() {
        // We are getting data after Site has been loaded
        axios.get('https://littleblog-c8a97.firebaseio.com/entry.json')
                .then(response => (this.entry = response));        
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

.biog, .achievement {
    background-color: rgba(0,0,0, 0.5);
    padding: 2%;
    margin: 0 0 20px 0;
}

</style>
