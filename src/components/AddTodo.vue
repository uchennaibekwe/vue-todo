<template>
    <div>
        <form @submit.prevent="addTodo">
            <input type="text" name="title" v-model="title" placeholder="Add Todo ..." required/>
            <input type="submit" v-bind:value="submitButtonValue" class="btn">
        </form>
    </div>
</template>

<script>
// import { v4 as uuidv4 } from 'uuid';
export default {
    name: "AddTodo",
    props: ["submitButtonValue"],
    data() {
        return {
            title: '',
        }
    },
    methods: {
        addTodo() {
            // e.preventDefault();
            if (this.title.trim().length < 1) {
                alert('No Todo Entered!');
                return false;
            }
            
            const newTodo = {
                // id: uuidv4(),
                title: this.title,
                completed: false,
            };
            // send up to parent
            this.$emit('add-todo', newTodo);
            this.title = ''
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }
</style>