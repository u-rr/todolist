<template>
    <div>
        <v-toolbar dark color="indigo">
            <router-link to="/">
                <v-icon>arrow_back</v-icon>
            </router-link>
            <v-toolbar-title class="white--text">
                Todoを入力してね！
            </v-toolbar-title>
        </v-toolbar>
        <v-text-field v-model="newTodo" placehlder="Input here..."></v-text-field>
        <v-btn dark color="indigo" v-on:click="addTodo()" class="white--text">
            送信
        </v-btn>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                newTodo: ''
            }
        },
        methods: {
            addTodo() {
                if(this.newTodo === '') return;
                const todos = JSON.parse(localStorage.getItem('todos')) || [];
                todos.push(this.newTodo);
                localStorage.setItem('todos', JSON.stringify(todos));
                this.newTodo = '';
                this.$router.push('/');
            }
        }
    }
</script>
<style scoped>
a {
    text-decoration: none;
}
</style>