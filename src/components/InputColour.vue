<script>
export default {
  props: {
    label: {
      type: String,
      required: true,
    }
  },
  data() {
    return{
      colour: "#000000"
    }
  },
  methods: {
    setColour() {
      this.$emit("colour-from-input", this.colour)
    }
  }
}
</script>

<template>
    <div>
      <div>
        <label  for="colour-input"><p class="colour-picker-label">{{ label }}: </p></label>
        <input
          type="color"
          id="colour-input"
          class="colour-picker"
          v-model="colour"
          @change="setColour"
        />
        <br/>
        <p class="colour-picker-colour">{{ colour.toUpperCase() }}</p>
      </div>
    </div>
</template>

<style>
.colour-picker {
  border: none;
	width: 11rem;
	height: 11rem;}

.colour-picker-label {
  text-align: center;
  font-weight: bold;
}

.colour-picker-colour {
  text-align: center;
}

@media (max-width: 768px ) {

  .colour-picker {
    padding: none;
    margin: none;
  }

}

</style>
