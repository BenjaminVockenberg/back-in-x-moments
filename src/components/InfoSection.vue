<template>
<div class="container">
    <div class="row align-items-center">
    
        <div class="col-sm-1">
            <i class="fas fa-info-circle" @click="show = !show"></i>
        </div>
        
        <transition name="fade">
            <div v-show="show" class="col-md-12 infoc" mode="out-in" @click="show = !show">
                <div class="row justify-content-center">
                    <div class="col-sm-4">
                        <h2>Hi I'm Ben</h2>
                        <h3>Frontend developer @Reservix in Frankfurt, Germany</h3>
                        <p>This site is not using any cookies, tracking or other malware. Enjoy!</p>
                        <p>This Site was made with Vue/Cli, Webpack and Love</p>
                        <p>Was using VSCode as my favorite IDE... try the <strong>ActionMode</strong> plugin if you want some action while coding :)</p>
                    </div>
                    <div class="col-sm-4">
                        <h2>Contact me</h2>
                        <h3>On Twitter or by email</h3>
                        <p><strong>Twitter:</strong> @technokrat</p>
                        <p><strong>Mail:</strong> benjamin.vockenberg@gmail.com</p>
                    </div>
                </div>
            </div>
        </transition>

    </div>
</div>
</template>

<script>
export default {
    name: 'InfoSection',
    data() {
        return {
            show: false
        }
    }
}
</script>

<style scoped lang="scss">
    i {
        font-size: 25px;
        color: rgba( 220, 220, 220, 0.5 );

        &:hover {
            color: rgba( 220,  220,220, 1 );
        }
    }

    p {
        color: whitesmoke !important;
    }

    .infoc {
        background-color: rgba( 0, 0, 0, 0.9 );
        padding: 5%;
        height: 100%;
        width: 100%;
        position: fixed;
        top: 0;
        left: 0;
        z-index: 999;
    }

    .fade-enter-active, .fade-leave-active {
        transition: opacity .5s;
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
        opacity: 0;
    }
    
</style>
