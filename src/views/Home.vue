<template>
  <div id="app">
    <br/>
    <h3>Public Key to p2pkh converter</h3>
    <PublicKeyConverter />

    <br/>
    <h3>Get Balance</h3>
    <Balance />
    
    <br/><br/>
    <h3>The Last 3 Ethereum Blocks</h3>
    <BitcoinBlocks />
  </div>
</template>

<script>
import BitcoinBlocks from '../components/BitcoinBlocks';
import Balance from '../components/Balance';
import PublicKeyConverter from '../components/PublicKeyConverter';

export default {
  name: 'Home',
  components: {
    BitcoinBlocks,
    Balance,
    PublicKeyConverter
  },
  methods: {},
  created() {}
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
    text-align: center;
  }

  .btn {
    display: inline-block;
    border: none;
    background: rgb(4, 172, 163);
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
