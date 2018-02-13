<template>
    <div class="clear">
        <i class="fa fa-trash-o" v-on:click="clear"></i>
    </div>
</template>

<script>
export default {
    name: 'Clear',

    methods: {
        clear() {
            this.$emit('removeAll');   
        }
    }
}
</script>

<style>
    .clear {
        color: orange;
        font-size: 80px;
    }
</style>