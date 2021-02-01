<template>
    <div>
        <form v-on:submit.prevent="addTodo" method="post">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
        <button class="clearbtn"  @click="clearCompleted" >Clear Completed</button>
        <button @click="clearAll">Clear All</button>
    </div>
</template>

<script>
// import uuid from 'uuid';
import { v4 } from 'uuid';
export default {
    name: "AddTodo",
    data() {
        return{
            title: '',
        }
    },
    methods: {
        addTodo() {
           
            const newTodo = {
                id: v4(),
                title: this.title,
                completed: false
            }

            // Send up to parent
            this.$emit('add-todo', newTodo);

            this.title = '';
        },
        clearCompleted() {
            const completedTodo = {
                completed: true
            }
            this.$emit('todo-done', completedTodo);
        },
        clearAll() {
            this.todo = [];
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
input[type="submit"] {
    flex: 2;
}
</style>