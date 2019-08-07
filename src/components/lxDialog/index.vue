<template>
    <div v-show="value" ref="drag" class="admin-box" :style="{left: cardLeft, right: right, top: cardTop, width: width}">
        <div class="moveHeader"
             @mousedown.prevent.stop="moveStart"
             @mousemove.prevent.stop="moveMove"
             @mouseup.prevent.stop="isMove = false"
             @mouseout.prevent.stop="isMove = false"></div>
        <div class="admin-close" @click="$emit('input', false)">&#10005;</div>
        <slot></slot>
    </div>
</template>

<script>
    export default {
        props: {
            value: Boolean,
            title: String,
            top: String,
            right: String,
            left: String,
            width: {
                type: String,
                default: '800px'
            }
        },
        data(){
          return{
              cardLeft:this.left|| null,
              cardTop:this.top || null,
              isMove: false
          }
        },
        methods:{
            moveStart (event) {
                let _el = this.$refs.drag
                this.beforeMove = {
                    top: _el.offsetTop - event.clientY,
                    left: _el.offsetLeft - event.clientX
                }
                this.isMove = true
            },
            moveMove (event) {
                if (!this.isMove) return false
                this.cardLeft = this.beforeMove.left + event.clientX + 'px'
                this.cardTop = this.beforeMove.top + event.clientY + 'px'
            }
        }
    }
</script>

<style scoped lang="scss">
    .admin-box {
        padding:15px 12px;
        position: absolute;
        z-index: 999;
        /*top: 180px;*/
        /*left: 520px;*/
        box-shadow: 0 0 20px inset rgba(18,81,125,1);
        background: rgba(2, 24, 54, .9);
        border-radius: 5px;
        .moveHeader{
            background: transparent;
            width: 100%;
            height: 70px;
            position: absolute;
            left: 0;
            top: 0;
            cursor: move;
            z-index: 5;

        }
        .admin-close {
            color: #02a9d7;
            width: 20px;
            height: 22px;
            text-align: center;
            position: absolute;
            top: 5px;
            right: 5px;
            cursor: pointer;
            z-index: 9;
        }
        .admin-close:hover {
            transform: scale(1.1);
        }
    }
</style>
