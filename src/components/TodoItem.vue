<template>
    <div class="todo-item" v-bind:class="{'is-complete': todo.completed }">
        <p>
            <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
            {{ todo.title }}
            <button class="del" @click="$emit('del-todo', todo.id)">&times;</button>
        </p>
    </div>
</template>

<script>
    export default {
        name: 'TodoItem',
        props: ["todo"],
        methods: {
            markComplete() {
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    .todo-item {
        background : #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: #a72424;
        color: #fff;
        border: none;
        padding: 2px 6px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>