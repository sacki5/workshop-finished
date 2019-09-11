<template>
    <div id="employeeForm">
        Name: <input v-model="employee.name" /><br>
        Email: <input v-model="employee.email" /><br>
        <button @click="submit">Submit</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            employee: {
                name: '',
                email: '',
            },
        };
    },
    methods: {
        submit() {
            this.$emit('add:employee', this.employee);
        },
    },
};
</script>
