<template>
    <div class="box" :data-name="name" :class="{ 'box--green': isAccepted }" :draggable="isDraggable" v-on:dragstart="onDragStart">
        <strong>{{name}}</strong>
    </div>
</template>

<script>
    export default {
        name: "Box",
        props: {
            name: String,
            isDraggable: {
                type: Boolean,
                default: false
            },
            isAccepted: {
                type: Boolean,
                default: false
            },
            onDragStart: {
                type: Function,
                default: function () {}
            }
        }
    };
</script>

<style scoped>
    .box {
        align-items: center;
        background-color: blue;
        display: flex;
        justify-content: center;
        height: 80px;
        width: 80px;
    }

    .box.box--green {
        background-color: green;
    }

    .box {
        cursor: pointer;
    }

    .box:not(:last-child) {
        margin-bottom: 10px;
    }

    strong {
        color: white;
        text-align: center;
    }
</style>
