<template>
  <v-container>
    <v-row>
      <v-col>
        <div>
          <h1>Ready canvas</h1>
          <v-card class="d-inline-block mx-auto" elevation="6" :width="1250">
            <p class="pa-3">Helper little functions for you later :)</p>
            <canvas
              id="myCanvas"
              ref="myCanvas"
              width="1200"
              height="1200"
              style="border:1px solid #000000;"
            ></canvas>
          </v-card>
        </div>
      </v-col>
      <v-col>
        <div>
          <h1>Canvas tool</h1>
          <v-stepper vertical>
            <v-stepper-step step="1" complete
              >Pick color for canvas border</v-stepper-step
            >

            <v-stepper-content step="1">
              <v-color-picker class="ma-2" canvas-height="200"></v-color-picker>
            </v-stepper-content>

            <v-stepper-step step="2" complete
              >Pick color for brush</v-stepper-step
            >

            <v-stepper-content step="2">
              man
              <!-- <v-color-picker class="ma-2" canvas-height="200"></v-color-picker> -->
            </v-stepper-content>
            <v-stepper-step step="3" complete>Start drawing!</v-stepper-step>
            <v-stepper-content step="3"
              >just something functions</v-stepper-content
            >
          </v-stepper>
        </div>
      </v-col>
    </v-row>

    <div></div>
  </v-container>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Main",

  data: () => ({})
});
</script>

<style scoped>
#myCanvas {
  display: inline;
  position: relative;
}
</style>
