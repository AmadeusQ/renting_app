<template>
  <div id="map-container"></div>
</template>

<script>
import { load } from "@2gis/mapgl";

export default {
  name: "TestPage",
  data() {
    return {
      map: null,
      marker: null,
    };
  },
  async mounted() {
    try {
      const mapglAPI = await load();

      // Initialize the map
      this.map = new mapglAPI.Map("map-container", {
        center: [55.31878, 25.23584],
        zoom: 13,
        key: "Your API access key",
      });

      // Add a marker to the map
      this.marker = new mapglAPI.Marker(this.map, {
        coordinates: [55.31878, 25.23584],
      });
    } catch (error) {
      console.error("Error loading map:", error);
    }
  },
  beforeUnmount() {
    if (this.marker) {
      this.marker.remove();
    }
    if (this.map) {
      this.map.remove();
    }
  },
};
</script>
