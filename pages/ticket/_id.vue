<template>
  <section>
    <header
      class="page--header ticket events flex flex-col justify-center items-center"
      :style="eventBG"
    >
      <div class="container flex flex-col justify-center">
        <h4>Google Extended meetup</h4>
        <div class="text-sm breadcrumbs">
          <ul>
            <li><nuxt-link to="/">Home</nuxt-link></li>
            <li><nuxt-link to="/events">Explore Event</nuxt-link></li>
            <li class="text-primary">Ticket</li>
          </ul>
        </div>
      </div>
    </header>
    <main>
      <section class="home--body">
        <div class="cto--container container relative px-4 min-h-screen">
          <div class="ticket--set">
            <div class="grid--collection">
              <ticket-card-grid v-if="activeTokens" :grid-size="2" />
            </div>
            <div v-if="activeTokens.length" class="ticket--data sticky top-0">
              <div class="card">
                <div class="card-body">
                  <h2 class="card-title">Ticket Summary</h2>
                  <div class="divider my-3"></div>
                  <div class="form-control w-full">
                    <label class="label">
                      <span class="label-text">Ticket Name</span>
                    </label>
                    <input
                      type="text"
                      disabled
                      :value="activeTokens[0].title"
                      class="input bg-base-100/10 w-full"
                    />
                  </div>
                  <div class="form-control mt-2 w-full">
                    <label class="label">
                      <span class="label-text">Ticket Description</span>
                    </label>
                    <textarea
                      disabled
                      rows="3"
                      class="textarea bg-base-100/10"
                      :value="activeTokens[0].description"
                    />
                  </div>
                  <div class="form-control mt-2 w-full">
                    <label class="label">
                      <span class="label-text">Created By</span>
                    </label>
                    <input
                      type="text"
                      disabled
                      :value="activeTokens[0].minter"
                      class="input bg-base-100/10 w-full"
                    />
                  </div>
                  <!--                  <div class="form-control mt-2 w-full">
                    <label class="label">
                      <span class="label-text">Owner</span>
                    </label>
                    <input
                      type="text"
                      disabled
                      value="Obani.testnet"
                      class="input bg-base-100/10 w-full"
                    />
                  </div>-->
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </section>
</template>

<script>
import { mapWritableState } from 'pinia'
import { useStore } from '@/store'

export default {
  setup() {
    const store = useStore()

    return { store }
  },
  computed: {
    eventBG() {
      if (this.activeTokens.length) {
        if (this.activeTokens[0].reference_blob?.animation_url) {
          return `background: url(${this.activeTokens[0].reference_blob?.animation_url})`
        }
      }
      return ''
    },
    ...mapWritableState(useStore, [
      'wallet',
      'details',
      'isConnected',
      'loading',
      'stores',
      'activeTokens',
    ]),
  },
  async mounted() {
    await this.store.fetchNftTokens(`${this.$route.params.id}`)
  },
}
</script>

<style lang="scss">
.ticket--btns {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  .btn {
    text-transform: none;
    margin-top: 10px;
  }
  .ticket--btn {
  }
}

.ticket--set {
  //position: relative;
  display: grid;
  grid-template-columns: 2.3fr 1.3fr;
  grid-gap: 20px;
  position: relative;
}
.ticket--data {
  position: sticky;
  top: 0;
}
</style>
