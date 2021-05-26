<template>
  <div class="home">
    <!--v-parallax
      src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
    -->
      <v-row
        align="center"
        justify="center"
      >
        <v-col
          class="text-center"
          cols="12"
        >
          <Generator></Generator>
        </v-col>
      </v-row>
    <!--/v-parallax-->
    <LinkFooter></LinkFooter>
  </div>
</template>

<script>
import Generator from '../components/IdGenerator'
import LinkFooter from '../components/LinkFooter'

export default {
  name: 'Home',
  components: {
    Generator,
    LinkFooter,
  }
}
</script>

<style scoped>

</style>