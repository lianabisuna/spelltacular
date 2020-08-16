<template>
  <v-btn
    tile
    :color="(vowel) ? '#add8e6' : 'white'"
    style="height: unset"
  >
    <v-container>
      <v-row align="center" justify="center">
        <img :src="image" :alt="alt">
      </v-row>
      <v-row align="center" justify="center">
        <div class="display-2 font-weight-black">{{ letter  }}</div>
      </v-row>
    </v-container>
  </v-btn>
</template>

<script>
export default {
  name: "Tile",

  props: {
    image: { type: String, required: true },
    vowel: { type: Boolean, required: true },
    letter: { type: String, required: true },
    alt: { type: String, required: true }
  },

  data: () => ({
    //
  })
};
</script>

<style lang="stylus">

</style>