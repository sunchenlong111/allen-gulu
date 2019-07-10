<template>
    <svg class="icon">
        <use :xlink:href=`#i-${name}`></use>
    </svg>
</template>
<script>
    export default {
        props:{
            name:{
                type:String,
                default:""
            }
        }
    }
</script>
<style lang="scss">
    .icon { width: 1em;height: 1em; }
</style>