<template>
    <div>
        <v-toolbar dark color="pink lighten-3">
            <v-toolbar-title class="white--text">
                ゆーるるのTodoリスト
            </v-toolbar-title>
        </v-toolbar>
        <v-list>
            <template v-for="(todo, i) in todos">
                <v-list-tile v-bind:key="i">
                    <v-list-tile-content>
                        {{ todo }}
                    </v-list-tile-content>
                    <v-list-tile-action>
                        <v-btn flat icon v-on:click="deleteTodo(i)">
                            <v-icon>delete</v-icon>
                        </v-btn>
                    </v-list-tile-action>
                </v-list-tile>
                <v-divider v-bind:key="i"></v-divider>
            </template>
        </v-list>

        <div class="bittom-right">
            <v-btn fab color="pink lighten-3" v-on:click="addTodo">
                <v-icon color="white">add</v-icon>
            </v-btn>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                todos: []
            }
        },
        created() {
            this.todos = JSON.parse(localStorage.getItem('todos')) || [];
        },
        methods: {
            deleteTodo(i) {
                this.todos.splice(i, 1);
                localStorage.setItem('todos', JSON.stringify(this.todos));
            },
            addTodo() {
                this.$router.push('/todos/add');
            }
        }
    }
</script>

<style scoped>

.bottom-right {
    position: fixed;
    bottom: 0;
    right: 0;
}

</style>