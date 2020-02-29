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
                @mousedown="onMouseDown($event)"
                @mousemove="onMouseMove($event)"
                @mouseup="onMouseUp($event)"
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
import Component from "vue-class-component";
@Component
export default class HelloWorld extends Vue {
  bgColor = "#619CE8";
  x = 0;
  y = 0;
  isDrawing = false;
  rect = {} as DOMRect;
  //canvas = this.$refs.myCanvas as HTMLCanvasElement;
  //ctx = this.canvas.getContext("2d");

  mounted() {
    this.initCanvas();
  }
  initCanvas() {
    const canvas = this.$refs.myCanvas as HTMLCanvasElement;
    const ctx = canvas.getContext("2d");
    this.rect = canvas.getBoundingClientRect();
    console.log("this is rect", this.rect, ctx);
  }
  onMouseDown(e) {
    this.x = e.clientX - this.rect.left;
    this.y = e.clientY - this.rect.top;
    this.isDrawing = true;
    console.log("mouse dow");
  }
  onMouseUp(e) {
    if (this.isDrawing === true) {
      this.drawLine(
        this.x,
        this.y,
        e.clientX - this.rect.left,
        e.clientY - this.rect.top
      );
      this.x = 0;
      this.y = 0;
      this.isDrawing = false;
      console.log("mouse up");
    }
  }
  onMouseMove(e) {
    if (this.isDrawing === true) {
      this.drawLine(
        this.x,
        this.y,
        e.clientX - this.rect.left,
        e.clientY - this.rect.top
      );
      this.x = e.clientX - this.rect.left;
      this.y = e.clientY - this.rect.top;
      console.log("mouse move");
    }
  }
  drawLine(x1: number, x2: number, y1: number, y2: number) {
    const canvas = this.$refs.myCanvas as HTMLCanvasElement;
    const ctx = canvas.getContext("2d") as CanvasRenderingContext2D;
    ctx.beginPath();
    ctx.strokeStyle = "black";
    ctx.lineWidth = 1;
    ctx.moveTo(x1, y1);
    ctx.lineTo(x2, y2);
    ctx.stroke();
    ctx.closePath();
    console.log("drawing line");
  }
}
</script>

<style scoped></style>
