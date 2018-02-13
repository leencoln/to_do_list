<template>
    <div class="inputBox">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" placeholder="할 일을 입력해 주세요">
        <i class="addBtn fa fa-plus"v-on:click="addTodo"></i>
    </div>
</template>

<script>
export default {
    name: 'TodoInput',

    data() {
        return {
            newTodoItem: ''
        }
    },

    methods: {
        addTodo() {
            if(this.newTodoItem) {
                let value = this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput();
            }
        },
        clearInput() {
            this.newTodoItem = '';
        }
    }

}
</script>

<style>
    .inputBox {
        background: white;
        height: 50px;
        border-radius: 5px;
    }

    .inputBox input {
        border-style: none;
        text-align: center;
        line-height: 45px;
    }

    .addBtn {
        float: right;
        line-height: 45px;
        margin-right: 10px;
        font-weight : 1000;
    }
</style>