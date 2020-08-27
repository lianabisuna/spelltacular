<template>
    <v-dialog
      v-model="dialog"
      max-width="290"
    >
      <v-card>
        <v-card-title class="headline">{{ word }}</v-card-title>

        <v-card-text>
          Let Google help apps determine location. This means sending anonymous location data to Google, even when no apps are running.
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            color="primary"
            text
            @click="dialog = false"
          >
            Alright!
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>

<script>
export default {
  name: "Modal",
  props: {
    dialog: { type: Boolean },
    word: { type: String },
  },
  data: () => ({
    //
  })
};
</script>