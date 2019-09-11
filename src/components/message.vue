<template>
    <div id="message">
        <input v-model="message" @keydown.enter="submit(message)"/>
        <button @click="submit(message)">Submit</button>
    </div>
</template>

<script>
export default {
    props: {
        defaultMessage: { type: String, default: '' },
    },
    data() {
        return {
            message: this.defaultMessage,
        };
    },
    methods: {
        submit(message) {
            this.message = '';
            this.$emit('add:message', message);
        },
    },
};
</script>
