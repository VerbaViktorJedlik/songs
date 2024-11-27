<template>
  <div id="app">
    <ArtistSelector :artists="artists" @artist-selected="fetchSongs"/>
    <SongList :songs="filteredSongs"/>
  </div>
</template>

<script>
import artistsData from '@/artists';
import songsData from '@/songs';

import ArtistSelector from './components/ArtistSelector.vue';
import SongList from './components/SongList.vue';

export default {
  name: 'App',
  components: {
    ArtistSelector,
    SongList
  },
  data() {
    return {
      // Az importált adatokat használjuk itt
      artists: artistsData,
      songs: songsData,
      filteredSongs: []
    };
  },
  methods: {
    fetchSongs(artistId) {
      // Szűrjük le a dalokat az ARTIST_ID alapján
      this.filteredSongs = this.songs.filter(song => song.ARTIST_ID === artistId);
    }
  }
};
</script>