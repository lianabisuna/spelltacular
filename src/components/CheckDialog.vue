<template>
    <v-dialog
      v-model="dialog"
      max-width="290"
    >
      <v-card>
        <sweet-alert-icon icon="success"></sweet-alert-icon>
        
        <v-card-title class="headline">{{ word }}</v-card-title>

        <v-card-text>what is meant by a word, text, concept, or action</v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            @click="dialog = false"
          >
            Alright!
          </v-btn>
          <v-spacer></v-spacer>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>

<script>
import SweetAlertIcon from 'vue-sweetalert-icons';
import Vue from 'vue';
Vue.use(SweetAlertIcon);

export default {
  name: "CheckDialog",
  props: {
    dialog: { type: Boolean },
    word: { type: String },
  },
  data: () => ({
    //
  })
};
</script>