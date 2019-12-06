<template>
    <table>
        <colgroup>
            <col style="width: 70px;" />
            <col />
            <col />
            <col />
            <col />
        </colgroup>
        <thead>
            <tr>
                <th></th>
                <th>Full Name</th>
                <th>Gender</th>
                <th>Address</th>
                <th>Email</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(employee, index) in employees" :key="index">
                <EmployeeTableCell
                    :componentType="CellType.IMAGE"
                    :value="employee.thumbnail"
                    :alt="employee.fullName"
                />
                <EmployeeTableCell
                    :value="employee.fullName"
                />
                <EmployeeTableCell
                    :value="employee.gender"
                />
                <EmployeeTableCell
                    :componentType="CellType.ADDRESS"
                    :value="employee.address"
                />
                <EmployeeTableCell
                    :componentType="CellType.EMAIL"
                    :value="employee.email"
                />
            </tr>
        </tbody>
    </table>
</template>

<script>
    import CellType from "../constants/cell-type";
    import EmployeeTableCell from "./EmployeeTableCell.vue";

    export default {
        name: "EmployeeTable",
        components: {
            EmployeeTableCell
        },
        data: function () {
            return {
                CellType
            };
        },
        props: {
            employees: Array
        }
    };
</script>

<style scoped>
    th {
        color: grey;
        font-size: 12px;
        font-weight: 700;
        line-height: 48px;
        padding: 0;
        text-align: left;
        text-transform: uppercase;
    }

    th:not(:first-child) {
        padding-right: 48px;
    }
</style>
