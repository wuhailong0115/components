<template>
    <div class="msg-swiper" @mouseover="stopTimer" @mouseout="createTimer"
         :style="{
           height: `${msHeight}px`,
           }">
        <div class="msg-swiper__msg" ref="msg-swiper__msg" :style="dirStyle1">
            <slot name="message1"></slot>
        </div>
        <div class="msg-swiper__msg" :style="dirStyle2">
            <slot name="message2"></slot>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        height: String,
        step: Number,
        time: Number,
        direction: {
            type: String,
            default: 'bottom'
        }
    },
    data () {
        return {
            timer: null,
            heights: 0,
            msHeight: this.height || 170,
            msStep: this.step || 1.2,
            msTime: this.time || 38,
            top1: 0,
            top2: 0,
            dirStyle1: {bottom: this.top1 + 'px'},
            dirStyle2: {bottom: this.top2 + 'px'}
        }
    },
    mounted () {
        let dom = this.$refs['msg-swiper__msg']
        this.heights = dom.clientHeight || dom.offsetHeight || dom.scrollHeight
        this.top2 = this.heights <= this.msHeight ? this.msHeight : this.heights
        this.createTimer()
    },
    methods: {
        createTimer () {
            if (this.heights <= this.msHeight) return false
            if (this.timer) return false
            this.timer = setInterval(() => {
                this.top1 -= this.msStep
                this.top2 -= this.msStep

                if ((this.top1 + this.heights) < 0) this.top1 = this.heights
                if ((this.top2 + this.heights) < 0) this.top2 = this.heights

                if (this.direction == 'top') {
                    this.dirStyle1 = {top: this.top1 + 'px'}
                    this.dirStyle2 = {top: this.top2 + 'px'}
                } else if (this.direction == 'bottom') {
                    this.dirStyle1 = {bottom: this.top1 + 'px'}
                    this.dirStyle2 = {bottom: this.top2 + 'px'}
                }
            }, this.msTime)
        },
        stopTimer () {
            clearInterval(this.timer)
            this.timer = null
        }
    }
}
</script>

<style lang="scss">
.msg-swiper {
    width: 100%;
    color: #fff;
    overflow: hidden;
    position: relative;
    .msg-swiper__msg{
        position: absolute;
        /*padding-bottom: 24px;*/
        transition: top 0s;
        transition-timing-function: ease-in;
    }
}
</style>
