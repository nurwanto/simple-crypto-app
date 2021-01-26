<template>
  <div>
    <table id="block-table">
      <thead>
        <tr>
          <th>Height</th>
          <th>Hash</th>
          <th>Miner</th>
          <th>Last Mined</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="block in blocks" :key="block.number">
          <td>{{block.number}}</td>
          <td>{{block.hash}}</td>
          <td>{{block.miner}}</td>
          <td>{{block.last_mined}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "BitcoinBlocks",
  components: {
  },
  data() {
    return {
      blocks: []
    }
  },
  created: async function () {
        const Web3 =  require('web3');
        var web3 = new Web3('https://mainnet.infura.io/v3/<SET YOUR ID>');
    
        const latest = await web3.eth.getBlockNumber()
        const size = 3;
        for (let i=0; i< size; i++) {
          const block = await web3.eth.getBlock(latest-i);
          const d = new Date(0)
          d.setUTCSeconds(block.timestamp);
          this.blocks.push({number: block.number, hash: block.hash, miner: block.miner, last_mined: d.toLocaleString()})
        }

    },
  methods: {}
}
</script>

<style scoped>
  table {
    font-family: arial, sans-serif;
    border-collapse: collapse;
    width: 60vw;
    height: auto;
    margin-left: 20vw;
    margin-right: 20vw;
    table-layout: fixed;
  }

  td, th {
    word-break: break-all;
    border: 1px solid #c7c6c6;
    text-align: left;
    padding: 8px;
  }

  thead > tr {
    background-color: #e9e6e6;
  }
</style>
