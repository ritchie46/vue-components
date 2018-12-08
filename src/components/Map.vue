<template>
    <div class="vue-component-map" v-bind:id="id" v-bind:style="{ height: mapHeight + 'px' }">
    </div>
</template>

<script>
    import L from 'leaflet'

    export default {
        name: "Map",

        props: {
            id: String,
            centerLatLong: Array,
            mapHeight: String,
            initMapProperties: Object,
        },

        data: function () {
            return {
                map: null,
                tileLayer: null,
            }
        },

        mounted() {
            this.initMap()
        },

        methods: {
            initMap: function () {
                this.map = L.map(this.id, this.initMapProperties).setView(new L.LatLng(this.centerLatLong[0],
                    this.centerLatLong[1]), 7.5);

                // create the tile layer with correct attribution
                let osmUrl = 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png';
                let osmAttrib = 'Map data © <a href="https://openstreetmap.org">OpenStreetMap</a> contributors';
                this.tileLayer = new L.TileLayer(osmUrl, {minZoom: 5, maxZoom: 20, attribution: osmAttrib});
                this.tileLayer.addTo(this.map);
            }
        }
    }
</script>

<style src="../../node_modules/leaflet/dist/leaflet.css"></style>
