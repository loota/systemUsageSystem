<template>
  <div>
    <v-text-field
      v-model="meth"
      full-width
      label="Kirjoita järjestelmän vaatima tieto numerojärjestyksessä numerosta 1 lähtien. Järjestelmä vaatii tietoa numeroon 3 asti."
    />
    <v-btn @click="save">
      Luo persistentti entiteetti lomaketiedon pohjalta
    </v-btn>
    <v-btn @click="list">
      Tabuloi local storagen sisältö 
    </v-btn>

    <v-snackbar
      v-model="showMessage"
      top
    >
      Tietuesisällöt: {{ savedItems }}
    </v-snackbar>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      meth: null,
      savedItems: null,
      showMessage: false,
      oneDone: false,
      twoDone: false,
      threeDone: false
    }
  },
  methods: {
    save: function() {
      if (this.meth !== '1' && this.meth !== '2' && this.meth !== '3') {
        alert('Numerojärjestys on väärä')
        return
      }

      if (this.meth === '2') {
        if (!this.oneDone) {
          alert('Numerojärjestys on väärä')
          return
        }
      }

      if (this.meth === '3') {
        if (!this.twoDone) {
          alert('Numerojärjestys on väärä')
          return
        }
      }

      if (Math.random(1) < 0.3) {
        localStorage.setItem('meth', JSON.stringify(this.meth))
        if (this.meth === '1') {
          this.oneDone = true
        }
        if (this.meth === '2') {
          this.twoDone = true
        }
      }
      alert('Tieto tallennettu onnistuneesti!')
    },
    list: function() {
      this.savedItems = localStorage.getItem('meth')
      this.showMessage = true
    }
  }
}
</script>

<style>
.VuetifyLogo {
  width: 180px;
  transform: rotateY(560deg);
  animation: turn 3.5s ease-out forwards 1s;
}

@keyframes turn {
  100% {
    transform: rotateY(0deg);
  }
}
</style>
