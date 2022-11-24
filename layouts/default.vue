<template>
  <div class="main--bg">
    <nav-bar />
    <Nuxt />
    <nif-footer />
  </div>
</template>

<script>
import { mapWritableState } from 'pinia'
import { useStore } from '@/store'

export default {
  name: 'DefaultLayout',
  setup() {
    const store = useStore()

    return { store }
  },
  computed: {
    ...mapWritableState(useStore, ['userType']),
  },
  async mounted() {
    await this.store.setupWallet()
    await this.store.fetchNftTokensBySplit(
      this.$nuxt.$config.network === 'testnet'
        ? `aef.testnet`
        : 'niftiqet.utinifty.near'
    )
    this.userType =
      localStorage.getItem('userType') || sessionStorage.getItem('userType')
    if (!this.userType) {
      localStorage.setItem('userType', 'Creator')
      sessionStorage.setItem('userType', 'Creator')
      this.userType =
        localStorage.getItem('userType') || sessionStorage.getItem('userType')
    }
  },
}
</script>
<style lang="scss"></style>
