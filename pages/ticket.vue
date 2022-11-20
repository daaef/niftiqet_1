<template>
  <section>
    <header
      class="page--header ticket events flex flex-col justify-center items-center"
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
        <div class="cto--container container px-4 min-h-screen">
          <div class="ticket--set">
            <div class="grid--collection">
              <div class="flex justify-between items-center">
                <h3 class="font-bold">Ticket Categories</h3>
                <select
                  class="select bg-primary text-base-content w-full max-w-xs"
                >
                  <option disabled selected>Select Category</option>
                  <option>VIP</option>
                  <option>VVIP</option>
                  <option>COUPLES</option>
                </select>
              </div>
              <event-card-grid :grid-size="2" />
            </div>
            <nuxt-child />
          </div>
        </div>
      </section>
    </main>
  </section>
</template>

<style lang="scss">
.ticket--set {
  //position: relative;
  display: grid;
  grid-template-columns: 2.3fr 1.3fr;
  grid-gap: 20px;
  .event--card-grid {
    margin-top: 20px !important;
  }
}
</style>
