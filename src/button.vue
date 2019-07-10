<template>
    <button class="g-button" :class="{[`icon-${iconPosition}`]:true}">
        <g-icon v-if="icon" :icon="icon"></g-icon>
        <div class="content">
            <slot></slot>
        </div>
    </button>
</template>

<script>
    export default {
        props: {
            icon:{
                type:String,
                default:''
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
    }
</style>