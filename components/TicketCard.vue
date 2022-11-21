<template>
  <div class="relative ticket--container">
    <a href="#" class="card event--card shadow-xl">
      <figure>
        <img :src="meta.reference_blob.media" alt="Shoes" class="rounded-xl" />
      </figure>
      <div class="card-body px-5 pt-5 text-left">
        <h3 class="font-medium text-md">{{ meta.title }}</h3>
        <p class="font-bold">
          {{
            meta.listings.length
              ? formatNearAmount(
                  Number(
                    meta.listings[meta.listings.length - 1].price
                  ).toLocaleString('fullwide', {
                    useGrouping: false,
                  })
                ) + ' NEAR'
              : 'Not Listed'
          }}
        </p>
      </div>
    </a>
    <div class="card-actionz">
      <div class="ticket--btns w-full">
        <NifBtn
          v-if="meta.listings.length && meta.owner !== details.accountId"
          class="btn w-full"
          >Buy</NifBtn
        >
        <button v-if="!meta.listings.length" class="btn w-full" @click="sell">
          Sell
        </button>
        <button class="btn w-full btn-error text-white">Burn</button>
      </div>
    </div>
    <b-modal
      v-model="sellTicket"
      has-modal-card
      trap-focus
      :destroy-on-hide="false"
      aria-role="dialog"
      aria-label="Example Modal"
      close-button-aria-label="Close"
      aria-modal
    >
      <template #default="props">
        <SellForm
          :store-id="meta?.nft_contract_id"
          :token-id="meta?.token_id"
          @close="props.close"
        />
      </template>
    </b-modal>
  </div>
</template>

<script>
import { formatNearAmount } from 'near-api-js/lib/utils/format'
import { mapWritableState } from 'pinia'
import { useStore } from '@/store'
export default {
  name: 'TicketCard',
  props: {
    self: {
      type: Boolean,
      default() {
        return false
      },
      required: false,
    },
    meta: {
      type: Object,
      default() {
        return {}
      },
      required: false,
    },
  },
  setup() {
    const store = useStore()
    return { formatNearAmount, store }
  },
  data() {
    return {
      sellTicket: false,
    }
  },
  computed: {
    ...mapWritableState(useStore, [
      'wallet',
      'details',
      'isConnected',
      'loading',
      'stores',
    ]),
  },
  methods: {
    sell() {
      this.sellTicket = true
    },
  },
}
</script>

<style lang="scss"></style>
