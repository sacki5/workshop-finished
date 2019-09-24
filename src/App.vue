<template>
    <div id="app">
        <employeeForm @add:employee="addEmployee" />
        <employeeTable
            :employees="employees"
            @delete:employee="deleteEmployee"
            @edit:employee="editEmployee"
        />
    </div>
</template>

<script>
import employeeForm from './components/employeeForm.vue';
import employeeTable from './components/employeeTable.vue';

export default {
    name: 'app',
    components: {
        employeeForm,
        employeeTable,
    },
    data() {
        return {
            employees: [],
        };
    },
    mounted() {
        this.getEmployees();
    },
    methods: {
        async getEmployees() {
            try {
                const response = await fetch('https://5d7f689015404800142245d4.mockapi.io/isac', {
                    method: 'GET',
                });
                const data = await response.json();
                this.employees = data;
            } catch (err) {
                console.error(err);
            }
        },


        async addEmployee(employee) {
            try {
                const response = await fetch('https://5d7f689015404800142245d4.mockapi.io/isac', {
                    method: 'POST',
                    body: JSON.stringify(employee),
                    headers: {
                        'Content-type': 'application/json; charset=UTF-8',
                    },
                });
                const data = await response.json();
                this.employees = [...this.employees, data];
            } catch (err) {
                console.error(err);
            }
        },

        async deleteEmployee(id) {
            try {
                await fetch(`https://5d7f689015404800142245d4.mockapi.io/isac/${id}`, {
                    method: 'DELETE',
                });

                this.employees = this.employees.filter(employee => employee.id !== id);
            } catch (err) {
                console.error(err);
            }
        },

        async editEmployee(employee) {
            try {
                const response = await fetch(`https://5d7f689015404800142245d4.mockapi.io/isac/${employee.id}`, {
                    method: 'PUT',
                    body: JSON.stringify(employee),
                    headers: {
                        'Content-type': 'application/json; charset=UTF-8',
                    },
                });

                const data = await response.json();
                this.employees[this.employees.indexOf(employee)] = data;
            } catch (err) {
                console.error(err);
            }
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
