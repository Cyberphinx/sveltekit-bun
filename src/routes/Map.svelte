<script lang="ts">
    import { onMount } from "svelte";

    onMount(async () => {
        const Map = (await import("@arcgis/core/Map")).default;
        const MapView = (await import("@arcgis/core/views/MapView")).default;

        const map = new Map({
            basemap: "gray-vector",
        });

        const view = new MapView({
            container: "viewDiv",
            map: map,
        });

        view.when(() => {
            console.debug("Map loaded");
        });
    });
</script>

<div id="viewDiv" />

<style>
    @import "@arcgis/core/assets/esri/themes/light/main.css";

    #viewDiv {
        min-height: 500px;
    }
</style>
