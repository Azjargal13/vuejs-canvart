<template>
  <v-container>
    <v-row>
      <v-col>
        <div>
          <h1>Ready canvas</h1>
          <v-card class="d-inline-block mx-auto" elevation="6" :width="1250">
            <p class="pa-2">Helper little functions for you later :)</p>
            <div class="pa-1 ma-auto" align="center">
              <canvas
                v-bind:style="{
                  backgroundColor: bgColor
                }"
                id="myCanvas"
                ref="myCanvas"
                width="1200"
                height="1200"
              ></canvas>
            </div>
          </v-card>
        </div>
      </v-col>
      <v-col>
        <div>
          <h1>Canvas tool</h1>
          <v-stepper vertical>
            <v-stepper-step step="1" complete
              >Pick a color for canvas background</v-stepper-step
            >

            <v-stepper-content step="1">
              <v-color-picker
                hide-inputs
                class="ma-2"
                canvas-height="200"
                v-model="bgColor"
              ></v-color-picker>
              selected color is {{ bgColor }}
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

  data: () => ({
    bgColor: "#619CE8FF"
  })
});
</script>

<style scoped>
#myCanvas {
  margin-left: auto;
  margin-right: auto;
}
</style>
