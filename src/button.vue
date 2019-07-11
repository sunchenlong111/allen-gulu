<template>
    <button class="g-button" :class="{[`icon-${iconPosition}`]:true}" @click="$emit('click')">
        <g-icon v-if="loading" class='loading icon' name="loading"></g-icon>
        <g-icon v-if="icon && !loading" :name="icon" class="icon"></g-icon>
        <div class="content">
            <slot></slot>
        </div>
    </button>
</template>

<script>
    // import Vue from 'vue'
    import Icon from './icon'
    // Vue.component('g-icon',Icon)
    export default {
        components:{
          'g-icon': Icon
        },
        props: {
            icon:{
                type:String,
                default:''
            },
            loading:{
                type:Boolean,
                default:false
            },
            iconPosition:{
                type:String,
                default:'left',
                validator(value){
                    return value === 'left' || value === 'right'
                }
            }
        }
    }
</script>


<style lang="scss">
    @keyframes spin {
        0% {transform: rotate(0deg);}
        100% {transform: rotate(360deg);}
    }
    .g-button {
        height: var(--button-height);
        padding: 0 1em;
        font: inherit;
        border-radius: var(--border-radius);
        border: 1px solid var(--border-color);
        background: var(--button-bg);
        display: inline-flex;
        justify-content: center;
        align-items: center;
        vertical-align: middle;
        &:hover {border-color: var(--border-color-hover);}
        &:active {background: var(--button-active-bg);}
        &:focus {outline: none;}
        > .content{order: 2}
        > .icon{order:1;margin-right:0.3em;}
        &.icon-right{
            > .content{order: 1}
            > .icon{order:2;margin-left: 0.3em;margin-right: 0;}
        }
        .loading{
            animation: spin 1s infinite linear;
        }
    }
</style>