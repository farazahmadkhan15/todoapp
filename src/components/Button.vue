<template>
<div>
  <button @click="onclick()" :style="{backgroung : color}" class="btn">{{text}}</button>
</div>

</template>

<script>
export default {
    name : 'Button',
    props : {
        text : String,
        color : String
    },
    methods : {
        onclick() {
            this.$emit('toogle-add-task')
        }
    }

}
</script>

<style>

</style>