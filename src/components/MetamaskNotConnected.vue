<script>
export default {
  props: ["ethereum"],
  emits: ["accountConnect"],
  data() {
    return {
      isConnected: false,
      connectedAccounts: [],
      errorNumber: 0,
    }
  },
  methods: {
    requestAccount() {
      console.log(typeof(this.ethereum));
      this.ethereum.request({method: "eth_requestAccounts"}).then((accounts) => {
        this.connectedAccounts = accounts;
        this.isConnected = true;
      }).catch((error) => {
        this.errorNumber += 1;
      })
    }
  },
  watch: {
    isConnected(newValue) {
      if (newValue) {
        this.$emit("accountConnect", this.connectedAccounts)
      }
    }
  }
}
</script>

<template>
<button @click="requestAccount">Connect Account</button>
  <p v-if="errorNumber > 0">Failed to connect {{ errorNumber }}</p>
</template>

<style scoped>
</style>
