<template>
    <td>
        <img v-if="componentType === CellType.IMAGE" :src="value" :alt="alt" />
        <address v-else-if="componentType === CellType.ADDRESS">{{value}}</address>
        <a v-else-if="componentType === CellType.EMAIL" :href="`mailto:${value}`">{{value}}</a>
        <span v-else>{{value}}</span>
    </td>
</template>

<script>
    import CellType from "../constants/cell-type";

    export default {
        name: "EmployeeTableCell",
        data: function () {
            return {
                CellType
            };
        },
        props: {
            value: String,
            componentType: {
                type: String,
                default: CellType.COMMON
            },
            alt: {
                type: String,
                default: undefined
            }
        }
    };
</script>

<style scoped>
    td {
        font-size: 14px;
        vertical-align: middle;
    }

    img {
        border-radius: 50%;
        margin: 10px 0;
    }

    a {
        color: skyblue;
        text-decoration: none;
    }

    address {
        padding-right: 48px;
    }
</style>
