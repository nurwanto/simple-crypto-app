<template>
  <div>
    <form @submit.prevent="getBalance">
      <input type="text" v-model="address" name="address" placeholder="Enter the address...">
      <input type="submit" value="Submit" class="btn">
    </form>
    <div id="output_bal" hidden>
        <h4>Balance (Gwei):</h4>
        <p id="balance"></p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Balance",
  data() {
    return {
      address: ''
    }
  },
  methods: {
    getBalance() {
        if (this.address === undefined || this.address === '') {
            alert("Please enter the address!");
        } else {
            const Web3 =  require('web3');
            const web3 = new Web3('https://mainnet.infura.io/v3/<SET YOUR ID>');
            web3.eth.getBalance(this.address, (err, wei) => {
                document.getElementById("output_bal").style.display = "block";
                if (err) {
                    document.getElementById('balance').innerText = err;
                }
                document.getElementById('balance').innerText = web3.utils.fromWei(wei, 'Gwei');
            })
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

  #output_bal > p {
      color: green;
  }
</style>
