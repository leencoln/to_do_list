<template>
    <div id="list">
        <ul>
            <li v-for="(todoItem, index) in propsdata" :key="todoItem">
                <i class="liIcon fa fa-angle-right"></i>
                {{ todoItem }}
                <i class="removeBtn fa fa-times" type="button" v-on:click="remove (todoItem, index)"></i>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'List',

    props: ['propsdata'],

    methods: {
        remove(todoItem, index) {
            this.$emit('remove', todoItem, index);
        }
    }
}

</script>

<style>
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0px;
        text-align: left;
    }

    li {
        background: white;
        border-radius: 5px;
        height: 30px;
        margin: 1rem 0;
        padding: 0 1rem;
        line-height: 25px;
    }

    .liIcon {
        color: gray;
        margin-right: 10px;
        font-weight: 1000;
    }

    .removeBtn {
        color: orange;
        float: right;
        line-height: 25px;
    }
</style>