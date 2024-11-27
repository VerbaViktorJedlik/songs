<template>
    <div class="song-list">
      <table>
        <thead>
          <tr>
            <th>Title</th>
            <th>Artist</th>
            <th>Time</th>
            <th>BPM</th>
            <th>Year</th>
            <th>Genre</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="song in songs" :key="song._id">
            <td>{{ song.TITLE }}</td>
            <td>{{ getArtistName(song.ARTIST_ID) }}</td>
            <td>{{ song.TIME }}</td>
            <td>{{ song.BPM }}</td>
            <td>{{ song.YEAR }}</td>
            <td>{{ song.GENRE }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SongList',
    props: {
      songs: Array
    },
    methods: {
      // Kiválasztjuk az előadót az ARTIST_ID alapján
      getArtistName(artistId) {
        // Itt hívhatod meg az App.vue komponensből vagy egy másik adatforrásból az előadók nevét
        const artist = this.$root.artists.find(a => a._id === artistId);
        return artist ? artist.artist : 'Unknown Artist';
      }
    }
  };
  </script>
  
  <style scoped>
  /* Táblázat stílusok */
  .song-list {
    margin-top: 20px;
    overflow-x: auto; /* Ha a táblázat szélessége túl nagy, akkor görgethető lesz */
  }
  
  table {
    width: 100%;
    border-collapse: collapse;
  }
  
  table, th, td {
    border: 1px solid #ddd;
  }
  
  th, td {
    padding: 12px;
    text-align: left;
  }
  
  th {
    background-color: var(--primary-color);
  }
  
  td {
    font-size: 0.9rem;
  }
  </style>
  