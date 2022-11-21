<template>
  <div class="relative ticket--container">
    <a href="#" class="card event--card shadow-xl">
      <figure>
        <img :src="meta.reference_blob.media" alt="Shoes" class="rounded-xl" />
      </figure>
      <div class="card-body px-5 pt-5 text-left">
        <h3 class="font-medium text-md">{{ meta.title }}</h3>
        <p></p>
      </div>
    </a>
    <div class="card-actionz">
      <div class="ticket--btns w-full">
        <NifBtn v-if="meta.listings.length" class="btn w-full">Buy</NifBtn>
        <button v-if="!meta.listings.length" class="btn w-full">Sell</button>
        <button class="btn w-full btn-error text-white">Burn</button>
      </div>
    </div>
  </div>
</template>

<script>
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
}
</script>

<style lang="scss"></style>
