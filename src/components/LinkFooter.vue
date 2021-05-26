<template>
  <v-footer
    absolute
    tile
    padless
    class=""
  >
    <v-card
      class="flex"
      flat
      tile
      color="#fafafa"
    >
      <v-card-title >
        <p class="subheading grey--text text--darken-4">Get connected with us on social networks!</p>

        <v-spacer></v-spacer>

        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4 light-blue darken-3"
          dark
          icon
        >
          <v-icon size="24px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-title>
      
      <v-card-text class="py-2 grey--text text-center">
        {{ new Date().getFullYear() }} — <strong>@David Alonso - Fabian Villalobos</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
  export default {
    data: () => ({
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
    }),
  }
</script>

<style scoped>
    .app-footer{
        color: black;
    }
</style>