<template>
    <transition name="slide">
        <div class="sider" v-show="showSider">
            <slot></slot>
            <button @click="showSider=false">关闭</button>
         </div>
    </transition>
</template>

<script>
    export default {
        name: 'GuluSider',
        data(){
            return {
                showSider:true
            }
        }
    }
</script>

<style lang="scss" scoped>
    .slide-enter-active, .slide-leave-active {
        transition: all 1s;
    }
    .slide-enter, .slide-leave-to {
        margin-left: -150px;
    }
</style>