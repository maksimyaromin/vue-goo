<template>
    <div class="container">
        <div class="boxes boxes--source">
            <Box
                v-for="name in names"
                :key="name"
                :name="name"
                :isDraggable="true"
                :onDragStart="onDragStart"
            />
        </div>

        <button v-on:click="onClick" class="reset-button">Reset</button>

        <div
            class="boxes boxes--destination"
            v-on:dragover="onDragOver"
            v-on:drop="onDrop"
        >
            <Box
                v-for="name in acceptedNames"
                :key="name"
                :name="name"
                :isAccepted="true"
            />
        </div>
    </div>
</template>

<script>
    import Box from "./components/Box.vue";

    const namesDB = [
        'Maksim',
        'Good Kat',
        'Patrick O\'Brian'
    ];

    export default {
        name: "app",
        components: {
            Box
        },
        data: function () {
            return {
                names: [ ...namesDB ],
                acceptedNames: []
            }
        },
        methods: {
            onDragStart: function (event) {
                if (event.target) {
                    event.dataTransfer.setData(
                        'text/plain',
                        event.target.attributes.getNamedItem('data-name').value
                    );
                }
            },
            onDragOver: function (event) {
                event.preventDefault();
            },
            onDrop: function (event) {
                const name = event.dataTransfer.getData('text');

                this.names = this.names.filter(na => na !== name);
                this.acceptedNames = [
                    ...this.acceptedNames,
                    name
                ];

                event.dataTransfer.clearData();
            },
            onClick: function () {
                this.names = [ ...namesDB ];
                this.acceptedNames = [];
            }
        }
    }
</script>

<style>
    .container {
        display: flex;
        justify-content: space-between;
        margin: 20px auto;
        max-width: 798px;
    }

    .boxes {
        background-color: #E6E6E6;
        box-sizing: border-box;
        padding: 10px;
        width: 100px;
    }

    .reset-button {
        background: transparent;
        border: 0;
        border-radius: 0;
        box-shadow: 0 0 10px rgba(0, 0, 0, .2);
        cursor: pointer;
        font-weight: bold;
        outline: none!important;
        text-transform: uppercase;
    }
</style>
