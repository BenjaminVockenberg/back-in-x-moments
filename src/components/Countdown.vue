<template>
<div class="container">
    <div class="row align-items-center">
        
        <h1>Will be back in ...</h1>
        <br><br><br><br>

        <div class="col-sm-12">
            <div class="row">
                
                <div class="col-sm-3">
                    <div class="col-sm-12">
                        <div class="row">
                            <div class="col-sm-12 digit">
                                <p class="text-center">{{ days | two_digits }}</p>
                            </div>
                        </div>
                        <div class="row">
                            <div class="col-sm-12 unit">
                                <p class="text-center">DAYS</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="col-sm-3">
                    <div class="col-sm-12">
                        <div class="row">
                            <div class="col-sm-12 digit">
                                <p class="text-center">{{ hours | two_digits }}</p>
                            </div>
                        </div>
                        <div class="row">
                            <div class="col-sm-12 unit">
                                <p class="text-center">HOURS</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="col-sm-3">
                    <div class="col-sm-12">
                        <div class="row">
                            <div class="col-sm-12 digit">
                                <p class="text-center">{{ minutes | two_digits }}</p>
                            </div>
                        </div>
                        <div class="row">
                            <div class="col-sm-12 unit">
                                <p class="text-center">MINUTES</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="col-sm-3">
                    <div class="col-sm-12">
                        <div class="row">
                            <div class="col-sm-12 digit">
                                <p class="text-center">{{ seconds | two_digits }}</p>
                            </div>
                        </div>
                        <div class="row">
                            <div class="col-sm-12 unit">
                                <p class="text-center">SECONDS</p>
                            </div>
                        </div>
                    </div>
                </div>            
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'Countdown',
    // Ready function
    mounted() {
        window.setInterval(() => {
            this.now = Math.trunc((new Date()).getTime() / 1000);            
        },1000);
    },
    // Data object
    data() {
        return {
            // Current Time without decimal places
            now: Math.trunc((new Date()).getTime() / 1000),
            // Date when I will be back again
            date : Math.trunc((new Date( 'January 21, 2019 09:00:00')) / 1000)            
        }
    },   
    computed: {
        /**
         * @name seconds
         * @returns {Number}
         * @desc computing the seconds enddate - now % 60
         */
        seconds() {
            return (this.date - this.now) % 60;
        },
        /**
         * @name minutes
         * @returns {Number}
         * @desc computing the minutes date - now / 60 % 60
         */
        minutes() {
            return Math.trunc((this.date - this.now) / 60) % 60;
        },
        /**
         * @name hours
         * @returns {Number}
         * @desc computing the hours date - now / minutes / seconds % max hours / day
         */
        hours() {
            return Math.trunc((this.date - this.now) / 60 / 60) % 24;
        },
        /**
         * @name days
         * @returns {Number}
         * @desc computing the days date - now / minutes / seconds / days!
         */
        days() {
            return Math.trunc((this.date - this.now) / 60 / 60 / 24);
        }
    },
    filters : {
        //! no need for a mixin because filter only used on computed properties 
        /**
         * @name two_digits
         * @param value {Number}
         * @returns value {String}
         * @desc timer digits lowers than one will get an 0 as prefix
         */
        two_digits : function (value) {
            if (value.toString().length <= 1) {
                return '0'+value.toString();
            }
            return value.toString();
        }
    }
}
</script>

<style scoped lang="scss">
.digit {
    p {
        font-family: 'Exo', sans-serif;
        font-size: 800%;//120px;
    }
}

.unit {    
    p {        
        font-family: 'Oswald', sans-serif;
        font-size: 40px;
        color: rgb(40, 153, 91) !important;
    }
}

@media (min-width: 576px) {
    .digit {
        p {            
            font-size: 400%;//120px;
        }
    }

    .unit {    
        p {        
            font-size: 30px;        
        }
    }    
}

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) {
    .digit {
        p {            
            font-size: 600%;//120px;
        }
    }

    .unit {    
        p {
            font-size: 30px;        
        }
    }
}

// Large devices (desktops, 992px and up)
@media (min-width: 992px) {
    .digit {
        p {            
            font-size: 800%;//120px;
        }
    }

    .unit {    
        p {
            font-size: 40px;
        }
    }
}

// Extra large devices (large desktops, 1200px and up)
@media (min-width: 1200px) {
    .digit {
        p {            
            font-size: 800%;//120px;
        }
    }

    .unit {    
        p {
            font-size: 40px;
        }
    }
}
</style>
