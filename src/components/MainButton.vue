<template>
  <!-- <v-tooltip top>
    <template v-slot:activator="{ on, attrs }"> -->
      <v-btn
        tile
        dark
        :color="color"
        style="height: unset"
      >
        <!-- v-bind="attrs"
        v-on="on" -->
        <v-container>
          <v-row align="center" justify="center">
            <v-icon x-large class="pt-5 pb-2">{{ icon }}</v-icon>
          </v-row>
          <v-row align="center" justify="center">
            <div class="headline pb-5 pt-2 font-weight-bold text-uppercase">{{ caption }}</div>
          </v-row>
        </v-container>
      </v-btn>
    <!-- </template>
    <span>CLICK ME</span>
  </v-tooltip> -->
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

<style>
/* border animation loop https://stackoverflow.com/questions/41686503/css-border-transitions-infinite-animation-loop */
/* .main-button {
  background: none;
  border: 0;
  box-sizing: border-box;
  box-shadow: inset 0 0 0 2px #f45e61;
  color: #f45e61;
  font-size: inherit;
  font-weight: 700;
  margin: 1em;
  padding: 1em 2em;
  text-align: center;
  text-transform: capitalize;
  vertical-align: middle;
}
.draw {
  overflow: hidden;
  position: relative;
}
.draw::before, .draw::after {
  content: '';
  box-sizing: border-box;
  position: absolute;
  border: 2px solid transparent;
  width: 0;
  height: 0;
}
.draw::before {
  top: 0;
  left: 0;
  border-top-color: #60daaa;
  border-right-color: #60daaa;
  animation: border 2s infinite;
}
.draw::after {
  bottom: 0;
  right: 0;
  animation: border 2s 1s infinite, borderColor 2s 1s infinite;
}

@keyframes border {
  0% {
    width: 0;
    height: 0;
  }
  25% {
    width: 100%;
    height: 0;
  }
  50% {
    width: 100%;
    height: 100%;
  }
  100% {
    width: 100%;
    height: 100%;
  }
}
@keyframes borderColor {
  0% {
    border-bottom-color: #60daaa;
    border-left-color: #60daaa;
  }
  50% {
    border-bottom-color: #60daaa;
    border-left-color: #60daaa;
  }
  51% {
    border-bottom-color: transparent;
    border-left-color: transparent;
  }
  100% {
    border-bottom-color: transparent;
    border-left-color: transparent;
  }
} */
</style>