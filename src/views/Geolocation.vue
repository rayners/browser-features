<template>
<div>
    <button @click='doLocate'>Where am I?</button>

    <table align="center" v-if="location">
        <tr><td>Lat</td><td>{{ location.coords.latitude }}</td></tr>
        <tr><td>Lng</td><td>{{ location.coords.longitude }}</td></tr>
    </table>

    <button @click='startWatching'>Monitor me</button>
</div>
</template>

<script>
export default {
  name: "Geolocation",
  data() {
      return { location: null, watchID: null, positions: [] };
  },
  methods: {
      doLocate() {
          alert('Locating!');
          navigator.geolocation.getCurrentPosition(position => {
              console.log(position);
              this.location = position;
          })
      },
      startWatching() {
          this.watchID = navigator.geolocation.watchPosition(position => {
              this.positions.push(position);
          });
      }
  }
};
</script>
