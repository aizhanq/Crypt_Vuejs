<script>
import Input from './components/Input.vue'
import Selector from './components/Selector.vue'

export default {
  components: {
    Input,
    Selector
  },
  data() {
    return {
      amount: 0,
      cryptoFirst: '',
      cryptoSecond: '',
      error: ''
    }
  },
  methods: {
    changeAmount(val) {
       this.amount = val
    },
    setCryptoFirst(val) {
      this.cryptoFirst = val
    },
    setCryptoSecond(val) {
      this.cryptoSecond = val
    },
    convert() {
        if(this.amount <= 0) {
          this.error = 'Enter a number greater than 0';
          return;
        } else if(this.cryptoFirst == '' || this.cryptoSecond == '') {
          this.error = 'Select currency';
          return;
        } else if(this.cryptoFirst == this.cryptoSecond) {
          this.error = 'Select another currency';
          return;
        } 
        this.error = '';
    }
  }
}
</script>

<template>
<h1>CRYPTO</h1>
<Input :changeAmount="changeAmount" :convert="convert"/>
<p v-if="error != ''">{{ error }}</p>
<div className="selectors">
  <Selector :setCrypto="setCryptoFirst"/>
  <Selector :setCrypto="setCryptoSecond"/>
</div>
</template>

<style scoped>
.selectors {
  display: flex;
  justify-content: space-around;
  width: 700px;
  margin: 0 auto;
}
</style>