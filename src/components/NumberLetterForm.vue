<template>
  <v-container class="center-container">
    <h1 class="font-weight-black">LE JEU DU PENDU</h1>
    <h2 class="subtitle-1">Combien de lettres dans ton mot ? (4-21)</h2>
    <div class="position-number">
      <p class="size-number">{{ number }}</p>

      <div class="position-buttons">
        <v-btn
          x-small
          fab
          dark
          color="#007CC7"
          class="ma-2"
          elevation="0"
          @click="incrementNumber"
        >
          <v-icon dark> mdi-plus </v-icon>
        </v-btn>
        <v-btn
          x-small
          fab
          dark
          color="#203647"
          class="ma-2"
          elevation="0"
          @click="decrementNumber"
        >
          <v-icon dark> mdi-minus </v-icon>
        </v-btn>
      </div>
    </div>
    <v-btn x-large rounded dark color="#4DA8DA" class="ma-2" @click="onSubmit">
      Valider
    </v-btn>
  </v-container>
</template>
<script>
export default {
  name: "NumberLetterForm",

  data: () => ({
    number: 4
  }),

  methods: {
    incrementNumber() {
      if (this.number < 21) {
        this.number++;
      }
    },
    decrementNumber() {
      if (this.number > 4) {
        this.number--;
      }
    },
    onSubmit() {
      let letters = [];
      for (let i = 1; i <= this.number; i++) {
        letters.push({ position: i, value: "" });
      }
      this.$emit("submitted", letters);
    }
  }
};
</script>
<style>
.size-number {
  margin-bottom: 0 !important;
  margin-right: 5px;
  font-size: 75px;
  user-select: none;
}
.center-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column;
  height: 100vh;
  color: white;
}
.position-number {
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
}

.position-buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column;
}
.style-title {
  font-size: 40px;
  padding-bottom: 10px;
}
</style>