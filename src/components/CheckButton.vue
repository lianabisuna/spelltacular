<template>
  <v-btn
    tile
    :dark="!empty"
    :disabled="empty"
    color="blue"
    style="height: unset"
    @click="$emit('check')"
  >
    <v-container>
      <v-row align="center" justify="center">
        <v-icon x-large class="pt-5 pb-2">mdi-arrow-right</v-icon>
      </v-row>
      <v-row align="center" justify="center">
        <div class="headline pb-5 pt-2 font-weight-bold text-uppercase">Check</div>
      </v-row>
    </v-container>
  </v-btn>
</template>

<script>
export default {
  name: "CheckButton",
  props: {
    empty: { type: Boolean, required: true },
  },
  data: () => ({
    //
  })
};
</script>

<style lang="stylus">

</style>