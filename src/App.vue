<template>
    <div id="app">
        <h1>H1 from APP</h1>
        <SpreadSheet id="spreadsheet" v-bind:hotSettings="hotSettings"/>

        <button v-on:click="buttonClicked">click2</button>
        <Map id="mapid" map-height=300 v-bind:center-lat-long="centerLatLong"
        v-bind:init-map-properties="null"/>


    </div>
</template>

<script>
    import SpreadSheet from './components/SpreadSheet.vue'
    import Map from './components/Map.vue'

    export default {
        name: 'app',
        components: {
            SpreadSheet,
            Map
        },
        data: function () {
            return {
                hotSettings: {
                    data: [
                        ["2016", 10, 11, 12, 13],
                        ["2017", 20, 11, 14, 13],
                        ["2018", 30, 15, 12, 13]
                    ],
                    colHeaders: ["", "Ford", "Volvo", "Toyota", "Honda"],
                    filters: true,
                    dropdownMenu: true
                },

                // map settings
                centerLatLong: [52.092876, 5.104480]
            }
        },
        methods: {
            buttonClicked: function() {
                console.log(this.hotSettings.data)
            }
        }
    }
</script>


<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
