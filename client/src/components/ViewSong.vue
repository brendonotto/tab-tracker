<template>
  <v-layout>
    <v-flex xs6>
        <panel title="Song Metadata">
          <div>
            {{song.title}}
            {{song.artist}}
            {{song.genre}}
          </div>
        </panel>
    </v-flex>

    <v-flex xs6>

    </v-flex>

  </v-layout>
</template>

<script>
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'
export default {
  data () {
    return {
      song: null
    }
  },
  async mounted () {
    const songId = this.$store.state.route.params.songId
    this.song = (await SongsService.show(songId)).data
  },
  components: {
    Panel
  }
}
</script>

<style scoped>

</style>
