<template>
    <div class="number_animate" :style="fontStyle">{{currentValue}}</div>
</template>

<script>
    export default {
        props: {
            data: Number,
            speed: {
                type: Number,
                default: 700
            },
            fontStyle: {
                type: Object,
                default: () => {
                    return {
                        color: '#ffcd36',
                        fontSize: '20px'
                    }
                }
            }
        },
        watch: {
            data (newVal, oldVal) {
                this.setNumber(newVal, oldVal)
            }
        },
        data () {
            return {
                interval: null,
                timeout: this.speed,
                steps: 10,
                currentStep: 0,
                targetValue: this.data,
                originalValue: this.data,
                currentValue: this.data
            }
        },
        methods: {
            setNumber (newVal, oldVal) {
                this.currentStep = 0
                this.originalValue = oldVal || 0
                this.targetValue = newVal || 0

                clearInterval(this.interval)
                this.interval = setInterval(() => {
                    if (this.currentStep >= this.steps) {
                        clearInterval(this.interval)
                    }
                    this.currentValue = this.commas(this.getValue(this.currentStep / this.steps))
                    this.currentStep = this.currentStep + 1
                }, this.timeout / this.steps)
            },
            commas (val) {
                return Math.round(val).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
            },
            getValue (percent) {
                const diff = this.targetValue - this.originalValue
                return (diff * percent) + this.originalValue
            }
        },
        beforeDestroy () {
            this.interval = null
            clearInterval(this.interval)
        }
    }
</script>

<style scoped>
 .number_animate {
     transition: all 0.6s ease;
 }
</style>