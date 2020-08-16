<template>
  <v-btn
    tile
    dark
    :color="color"
    style="height: unset"
  >
    <v-container>
      <v-row align="center" justify="center">
        <v-icon x-large class="pt-5 pb-2">{{ icon }}</v-icon>
      </v-row>
      <v-row align="center" justify="center">
        <div class="headline pb-5 pt-2 font-weight-bold text-uppercase">{{ caption }}</div>
      </v-row>
    </v-container>
  </v-btn>
</template>

<script>
export default {
  name: "MainButton",
  props: {
    color: { type: String, required: true },
    icon: { type: String, required: true },
    caption: { type: String, required: true }
  },
  data: () => ({
    //
  })
};
</script>

<style lang="stylus">

</style>