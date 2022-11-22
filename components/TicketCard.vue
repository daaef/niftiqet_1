<template>
  <div class="relative ticket--container">
    <a
      href="#"
      class="card event--card shadow-xl"
      :class="meta?.burned_timestamp ? 'bg-error' : ''"
    >
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
      <div v-if="!meta?.burned_timestamp" class="ticket--btns w-full">
        <button
          v-if="meta.listings.length && meta.owner !== details.accountId"
          class="btn def--btn w-full"
          @click="buyTicket"
        >
          Buy
        </button>
        <button
          v-if="!meta.listings.length && meta.owner === details.accountId"
          class="btn w-full"
          @click="sell"
        >
          Sell
        </button>
        <button
          v-if="meta.owner === details.accountId"
          class="btn w-full btn-error text-white"
          @click="confirmBurn"
        >
          Burn
        </button>
      </div>
      <div v-else class="text-center">
        <h3 class="text-error text-3xl font-black">BURNED</h3>
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
    metaStuff() {
      return this.meta
    },
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
    burnTicket(_, token) {
      this.wallet
        ?.burn([`${this.meta?.token_id}`], this.meta?.nft_contract_id)
        .then((res) => {
          console.log('res is', res)
        })
        .catch(() => {
          this.$buefy.toast.open({
            duration: 5000,
            message: 'Failed to burn TIcket!',
            type: 'is-danger',
          })
        })
    },
    confirmBurn() {
      console.log('burning ticket')
      this.$buefy.dialog.confirm({
        title: 'Burning Ticket',
        message:
          'Are you sure you want to <b>Burn</b> this ticket? This action cannot be undone.',
        confirmText: 'Burn Ticket',
        type: 'is-danger',
        hasIcon: true,
        onConfirm: () => this.burnTicket(),
      })
    },
    buyTicket() {
      console.log('buying ticket')
      this.wallet?.makeOffer(
        `${this.meta?.token_id}:${this.meta?.nft_contract_id}`,
        Number(
          this.meta.listings[this.meta.listings.length - 1].price
        ).toLocaleString('fullwide', {
          useGrouping: false,
        })
      )
    },
  },
}
</script>

<style lang="scss">
.card.bg-error {
  background-color: hsl(var(--er) / 0.4);
}
.ticket--btns.hidden {
  display: none;
}
</style>
