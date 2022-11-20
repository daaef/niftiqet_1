<template>
  <div class="relative card activity--card">
    <img src="https://placeimg.com/400/225/arc" alt="Event Activity" />
    <div class="card--content">
      <h3>Deep Sea Plan</h3>
      <p>
        Deep Sea Plan (x Antoni Tudisco) #44/44 was put up for sale for 0.0991
        NEAR
      </p>
      <p>At: 10/07/2022</p>
      <p class="text-primary">by @sarawts</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'EventActivity',
  props: {
    self: {
      type: Boolean,
      default() {
        return false
      },
      required: false,
    },
  },
}
</script>

<style lang="scss">
.activity--card {
  display: grid;
  padding: 20px;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;
  border: solid 1px hsl(var(--bc));
  @media (max-width: 1024px) {
    grid-template-columns: 1fr;
  }
  h3 {
    font-weight: bold;
    font-size: 1.1rem;
    margin-bottom: 5px;
  }
  p:not(:last-child) {
    margin-bottom: 5px;
  }
  img {
    border-radius: 12px;
    height: 100%;
    width: 100%;
    object-fit: cover;
  }
  .card--content {
    align-self: center;
  }
}
</style>
