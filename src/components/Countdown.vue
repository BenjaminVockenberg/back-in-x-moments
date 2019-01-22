<template>
<div class="container">
    <div class="row align-items-center">
        
        <h1>I'll be back in ...</h1>
        <br><br>

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

    // former ready function
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

    methods: {
        /**
         * @name countZero
         * @returns {Bool}
         * @desc will set Countdown to zero if Date exspired 
         */
        countsZero() {
            if (this.date - this.now <= 0) {
                return true;
            }

            return false;
        }
    },

    computed: {        

        /**
         * @name seconds
         * @returns {Number}
         * @desc computing the seconds enddate - now % 60
         */
        seconds() {            
            if (!this.countsZero()) {
                return (this.date - this.now) % 60;
            }
            return 0;
            
        },

        /**
         * @name minutes
         * @returns {Number}
         * @desc computing the minutes date - now / 60 % 60
         */
        minutes() {
            if (!this.countsZero()) {
                return Math.trunc((this.date - this.now) / 60) % 60;
            }
            return 0;
        },

        /**
         * @name hours
         * @returns {Number}
         * @desc computing the hours date - now / minutes / seconds % max hours / day
         */
        hours() {
            if (!this.countsZero()) {
                return Math.trunc((this.date - this.now) / 60 / 60) % 24;
            }
            return 0;
        },

        /**
         * @name days
         * @returns {Number}
         * @desc computing the days date - now / minutes / seconds / days!
         */
        days() {
            if (!this.countsZero()) {
                return Math.trunc((this.date - this.now) / 60 / 60 / 24);
            }
            return 0;
        }
    },
    filters : {
        
        //! no need for a mixin because filter only used on computed properties 
        /**
         * @name two_digits
         * @param value {Number}
         * @returns value {String}
         * @desc putting a leading zero if number has digits < 2
         */
        two_digits : function (value) {
            if (value.toString().length <= 1) {
                return '0' + value.toString();
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
        font-size: 750%;
    }
}

.unit {
    p {
        font-family: 'Oswald', sans-serif;
        font-size: 40px;
        color: rgb( 40, 153, 91 ) !important;
    }
}

@media (min-width: 576px) {
    .digit {
        p {
            font-size: 400%;
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
            font-size: 600%;
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
            font-size: 750%;
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
            font-size: 750%;
        }
    }

    .unit {
        p {
            font-size: 40px;
        }
    }
}
</style>
