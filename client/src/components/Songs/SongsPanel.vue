<template>
  <v-layout column>
    <v-flex>
      <panel title="Songs">
        <v-btn
          slot="action"
          :to="{
            name: 'songs-create'
          }"
          class="cyan accent-2"
          light
          medium
          absolute
          right
          middle
          fab>
          <v-icon>add</v-icon>
        </v-btn>
        </div>
        <div
          v-for="song in songs"
          class="song"
          :key="song.id">

          <v-layout>
            <v-flex xs6>
              <div class="song-title">
                {{song.title}}
              </div>
              <div class="song-artist">
                {{song.artist}}
              </div>
              <div class="song-genre">
                {{song.genre}}
              </div>

              <v-btn
                dark
                class="cyan"
                :to="{
                  name: 'song',
                  params: {
                    songId: song.id
                  }
                }">
                View
              </v-btn>
            </v-flex>
            <v-flex xs6>
              <img :src="song.albumImageUrl" alt="" class="album-image">
            </v-flex>
          </v-layout>
        </div>
      </panel>
    </v-flex>
  </v-layout>
</template>

<script>
import SongsService from '@/services/SongsService'
export default {
  data () {
    return {
      songs: null
    }
  },
  watch: {
    '$router.query.search': {
      immediate: true,
      async handler (value) {
        this.songs = (await SongsService.index(value)).data
      }
    }
  },
  async mounted () {
    this.songs = (await SongsService.index()).data
    console.log('songs', this.songs)
  }
}
</script>

<style scoped>
.song {
  padding: 20px;
  height: 330px;
  overflow: hidden;
}

.song-title {
  font-size: 30px;
}

.song-artist {
  font-size: 24px;
}

.song-genre {
  font-size: 18px;
}

.album-image {
  width: 70%;
  margin: 0 auto;
}
</style>
