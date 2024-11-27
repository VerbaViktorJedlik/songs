<template>
    <div>
      <label for="artist-select">Válassz előadót:</label>
      <select id="artist-select" @change="onArtistChange">
        <option v-for="artist in artists" :key="artist._id" :value="artist._id">{{ artist.artist }}</option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ArtistSelector',
    props: {
      artists: Array
    },
    methods: {
      onArtistChange(event) {
        this.$emit('artist-selected', parseInt(event.target.value));
      }
    }
  };
  </script>
  