<template>
  <div>
    <v-layout>
      <v-flex xs4>
        <panel title="Song Metadata">
          <v-text-field
            label="Title"
            v-model="title"
          ></v-text-field>
          <v-text-field
            label="Artist"
            v-model="artist"
          ></v-text-field>
          <v-text-field
            label="Genre"
            v-model="genre"
          ></v-text-field>
          <v-text-field
            label="Album"
            v-model="album"
          ></v-text-field>
          <v-text-field
            label="Album Image Url"
            v-model="albumImageUrl"
          ></v-text-field>
          <v-text-field
            label="YouTube Id"
            v-model="youtubeId"
          ></v-text-field>
        </panel>
      </v-flex>

      <v-flex xs8>
        <panel title="Song structure" class="ml-2">
          <v-text-field
            label="Tab"
            multi-line
            v-model="tab"
          ></v-text-field>

          <v-text-field
            label="Lyrics"
            multi-line
            v-model="lyrics"
          ></v-text-field>
        </panel>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import Panel from '@/components/Panel'
export default {
  data () {
    return {
      title: null,
      artist: null,
      genre: null,
      album: null,
      albumImageUrl: null,
      youtubeId: null,
      lyrics: null,
      tab: null
    }
  },
  components: {
    Panel
  }
}
</script>

<style scoped>

</style>
