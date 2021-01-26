<template>
  <div>
    <form @submit.prevent="convert">
      <input type="text" v-model="pubkey" name="pubkey" placeholder="Enter the public key...">
      <input type="submit" value="Submit" class="btn">
    </form>
    <div id="output" hidden>
        <h4>p2pkh:</h4>
        <p id="p2pkh"></p>
    </div>
  </div>
</template>

<script>
export default {
  name: "PublicKeyConverter",
  data() {
    return {
      pubkey: ''
    }
  },
  methods: {
    convert() {
        if (this.pubkey === undefined || this.pubkey === '') {
            alert("Please enter the public key!");
        } else {
            const bitcoin = require('bitcoinjs-lib');
            const { address } = bitcoin.payments.p2pkh({ pubkey: new Buffer(this.pubkey, 'hex') });
            document.getElementById("output").style.display = "block";
            document.getElementById('p2pkh').innerText = address;
        }
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
    margin-left: 20vw;
    margin-right: 20vw;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px;
  }

  input[type="submit"] {
    flex: 2;
  }

  #output > p {
      color: green;
  }
</style>
