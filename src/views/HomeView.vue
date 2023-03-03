<script>
import InputColour from '@/components/InputColour.vue'
import ContrastRatio from '@/components/ContrastRatio.vue'
import ccc from '../contrast.js'

export default {
  components: {
    InputColour,
    ContrastRatio
  },
  data() {
    return {
      background: "#FFFFFF",
      foreground: "#000000",
    }
  },
  methods: {
    setBackground(colour) {
      this.background = colour;
    },
    setForeground(colour) {
      this.foreground = colour;
    },
    checkIsLevelAA(c1, c2, fs) {
      return ccc.isLevelAA(c1, c2, fs);
    },
    checkIsLevelAAA(c1, c2, fs) {
      return ccc.isLevelAAA(c1, c2, fs);
    }
  }
}

</script>

<template>
  <div class="wrap" :style="{backgroundColor: background}">
    <div class="left">
      <div class="demo-background">
      <p class="demo-foreground" :style="{color: foreground}">Aa</p>
      </div>
      <div class="horizontal">
        <div>
          <ContrastRatio :background="background" :foreground="foreground"/>
        </div>
        <div class="stack">
          <div class="horizontal-wcag" >
            <div class="normal">
              WCAG Normal
            </div>
            <div class="large">
              WCAG Large
            </div>
          </div>
          <div class="horizontal">
            <div class="pass-fail" :style="{backgroundColor: checkIsLevelAA(background, foreground, 14) ? 'DarkSeaGreen' : 'LightCoral'}">
                  AA: {{ checkIsLevelAA(background, foreground, 14) ? 'Pass' : 'Fail'}}
                </div>
                <div class="pass-fail" :style="{backgroundColor: checkIsLevelAAA(background, foreground, 14) ? 'DarkSeaGreen' : 'LightCoral'}">
                  AAA: {{ checkIsLevelAAA(background, foreground, 14) ? 'Pass' : 'Fail'}}
                </div>
                <div class="pass-fail" :style="{backgroundColor: checkIsLevelAA(background, foreground, 18) ? 'DarkSeaGreen' : 'LightCoral'}">
                  AA: {{ checkIsLevelAA(background, foreground, 18) ? 'Pass' : 'Fail'}}
                </div>
                <div class="pass-fail" :style="{backgroundColor: checkIsLevelAAA(background, foreground, 18) ? 'DarkSeaGreen' : 'LightCoral'}">
                  AAA: {{ checkIsLevelAAA(background, foreground, 18) ? 'Pass' : 'Fail'}}
                </div>
          </div>
        </div>
      </div>
    </div>

  <div class="right">
    <div class="stack-input">
      <div class="inputColour">
        <InputColour label="Background" @colour-from-input="setBackground"/>
      </div>
      <div class="inputColour">
        <InputColour label="Foreground" @colour-from-input="setForeground"/>
      </div>
    </div>
  </div>

</div>
</template>


<style scoped>
/* .color-contrast-checker {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
} */

.demo-background {
  width: 100%;
  height:100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.demo-foreground {
  font-size: 11rem;
}

.large {
  font-size: 18pt;
  font-weight: bold;
  justify-content: center;
  align-content: center;
  text-align: justify;
  margin-left: 10px;
  padding-bottom: 5px;
  color: rgb(240, 240, 240);
}

.normal {
  font-size: 14pt;
  font-weight: bold;
  justify-content: center;
  align-content: center;
  text-align: justify;
  margin-right: 8px;
  color: rgb(240, 240, 240);
}

.wrap {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.left {
  flex: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 50px;
}

.right {
  height: 100%;
  background-color: whitesmoke;
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.horizontal {
  display: flex;
  flex-direction: row;
}

.stack {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  white-space: nowrap;
  margin-left: 10px;
  margin-right: 10px;
  color: black;
}

.horizontal-box {
  position: absolute;
  display: flex;
  flex-direction: row;
  bottom: 0px;
  white-space: nowrap;
}

.inputColour {
  margin: 1rem;
}

.stack-input {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  white-space: nowrap;
  margin-left: 10px;
  margin-right: 10px;
  color: black;
}

.horizontal-wcag {
  display: flex;
  flex-direction: row;
  width: 300px;
  justify-content: center;
  align-content: center;
  align-items: center;
  background-color: black;
}

.pass-fail {
  width: 75px;
  height: 25px;
  display: flex;
  justify-content: center;
  align-items: center;
}

@media (max-width: 768px ) {
  .wrap {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  }

  .right {
  display: flex;
  flex-direction: row;
  width: 100%;
  }

  .stack-input {
  display: flex;
  flex-direction: row;
  }
}


</style>
