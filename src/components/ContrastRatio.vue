<script>
import ccc from "../contrast.js";

export default {
  props: {
    background: {
      type: String,
      required: true,
    },
    foreground: {
      type: String,
      required: true,
    }
  },
  data() {
    return{
      ratio: 0
    }
  },
  methods: {
    getContrastRatio() {
        // calculate ratio
        var l1 = ccc.hexToLuminance(this.background);
        var l2 = ccc.hexToLuminance(this.foreground);
        return ccc.getContrastRatio(l1, l2).toFixed(2);
    }
  }
}
</script>

<template>
    <div class="circle">
      <p class="ratio"> Ratio: {{getContrastRatio()}}</p>
    </div>
</template>

<!-- .circle {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    font-weight: bold;
  } -->

<style>
.ratio {
  width: 125px;
  height: 125px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: rgb(240, 240, 240);
  font-weight: bold;
  background-color: black;
  margin: 1rem;
}
</style>
