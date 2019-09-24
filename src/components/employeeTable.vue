<template>
    <div id="employeeTable">
        <table>
            <tr>
                <th>Name</th>
                <th>Email</th>
            </tr>
            <tr v-for="(employee, index) in employees" :key="index">
                <td v-if="employee.id === edit"><input v-model="employee.name" /></td>
                <td v-else>{{ employee.name}}</td>

                <td v-if="employee.id === edit"><input v-model="employee.email" /></td>
                <td v-else>{{ employee.email}}</td>

                <td>
                    <button v-if="employee.id === edit" @click="editEmployee(employee)">
                        Save
                    </button>
                    <button v-else @click="edit = employee.id">Edit</button>
                    <button @click="$emit('delete:employee', employee.id)">Delete</button>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    props: {
        employees: Array,
    },
    data() {
        return {
            edit: null,
        };
    },
    methods: {
        editEmployee(employee) {
            this.$emit('edit:employee', employee);
            this.edit = null;
        },
    },
};
</script>
