<template>
    <div id="app">
        <message default-message="hej" @add:message="addMessage" />
        <list :items="messages" />
    </div>
</template>

<script>
import message from './components/message.vue';
import list from './components/list.vue';

export default {
    name: 'app',
    components: {
        message,
        list,
    },
    data() {
        return {
            messages: Array,
            test: String,
        };
    },

    methods: {
        addMessage(item) {
            this.messages.push(item);
        },
    },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
