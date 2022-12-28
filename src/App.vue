<script>
import MetamaskNotConnected from "@/components/MetamaskNotConnected.vue";
import MetamaskConnected from "@/components/MetamaskConnected.vue";

export default {
  components: {
    MetamaskConnected,
    MetamaskNotConnected,
  },
  data() {
    return {
      ethereum: window.ethereum,
      connectedAccounts: null
    }
  }
}

</script>

<template>
  <MetamaskNotConnected v-if="connectedAccounts === null" :ethereum="ethereum" @accountConnect="(accounts) => this.connectedAccounts=accounts"/>
  <MetamaskConnected v-if="connectedAccounts !== null" :connectedAccounts="connectedAccounts"/>
</template>

<style scoped>
</style>
