<template>
  <div v-if="events.length" class="">
    <div
      v-for="(event, i) in stor"
      :key="i"
      class="event--card-grid"
      :class="gridSize === 3 ? 'three' : 'two'"
    >
      <h3 v-if="event.length" class="capitalize font-medium text-xl">
        {{ event[0].nft_contract_name }} Store
      </h3>
      <div v-for="meta in event" :key="meta.id">
        <event-card :meta="meta" :self="linkSelf" />
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable no-prototype-builtins */
import { mapWritableState } from 'pinia'
import { useStore } from '@/store'

export default {
  props: {
    gridSize: {
      type: Number,
      default() {
        return 3
      },
    },
    linkSelf: {
      type: Boolean,
      default() {
        return false
      },
    },
    storeId: {
      type: String,
      default() {
        return ''
      },
    },
  },
  setup() {
    const store = useStore()

    return { store }
  },
  data() {
    return {
      events: [],
    }
  },
  computed: {
    stor() {
      return this.events.map((event) => {
        // eslint-disable-next-line array-callback-return
        return event
          .sort()
          .map((meta, i) => {
            if (i === 0) {
              return meta
            }
            if (meta?.title !== event[i - 1 < 0 ? 0 : i - 1].title) {
              return meta
            }
            return null
          })
          .filter((event) => {
            return event !== null
          })
      })
    },
    sortedStores() {
      return this.events.map((event) => {
        // eslint-disable-next-line no-return-assign,no-sequences
        return event
          .map((meta) => {
            if (meta?.listings?.length && this.userType === 'Buyer') {
              return meta
            } else if (this.userType === 'Creator') {
              return meta
            }
            return null
          })
          .filter((event) => {
            return event !== null
          })
      })
    },
    ...mapWritableState(useStore, [
      'wallet',
      'details',
      'isConnected',
      'loading',
      'stores',
      'metadata',
      'myStores',
      'userType',
    ]),
  },
  async mounted() {
    // await console.log('props',this.storeId)
    await this.store.fetchMetaData()
    if (this.myStores) {
      for (const key in this.myStores) {
        if (this.myStores.hasOwnProperty(key)) {
          // console.log(`${key}: ${this.myStores[key]}`)
          this.events.push(this.myStores[key])
          console.log(this.sortedStores)
        }
      }
    }
  },
}
</script>

<style scoped></style>
