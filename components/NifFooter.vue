<template>
  <footer class="bg-base-100/20 backdrop-blur py-20 px-4">
    <div class="container footer text-base-content">
        <div class="logo--set">
          <nuxt-link to="/" class="logo--link">
            <img src="/logo.png" class="logo--light" alt="">
            <img src="/logo-dark.png" class="logo--dark" alt="">
          </nuxt-link>
          <p>Decentralised NFTs Ticketing Mangement Solution</p>
          <div class="grid grid-flow-col gap-4">
            <nif-btn href="https://web.facebook.com" target="_blank">
              <span uk-icon="twitter"></span>
            </nif-btn>
            <nif-btn href="https://web.facebook.com" target="_blank">
              <span uk-icon="instagram"></span>
            </nif-btn>
            <nif-btn href="https://web.facebook.com" target="_blank">
              <span uk-icon="discord"></span>
            </nif-btn>
            <nif-btn href="https://web.facebook.com" target="_blank">
              <span uk-icon="youtube"></span>
            </nif-btn>
            <nif-btn href="https://web.facebook.com" target="_blank">
              <span uk-icon="tiktok"></span>
            </nif-btn>
          </div>
        </div>
        <div>
          <span class="footer-title">Resources</span>
          <a class="link link-hover">Stores</a>
          <a class="link link-hover">Marketplace</a>
          <a class="link link-hover">My Collections</a>
          <a class="link link-hover">Activity</a>
        </div>
        <div>
          <span class="footer-title">Check in</span>
          <a class="link link-hover">About</a>
          <a class="link link-hover">Contact</a>
          <a class="link link-hover">FAQs</a>
        </div>
    </div>
    <div class="container  pt-10 footer-center text-base-content">
      <div class="flex flex-col">
        <div class="grid max-w-sm grid-cols-2 mx-auto text-center link--divider">
          <a href="#">Terms</a>
<!--          <hr >-->
          <a href="#">Policies</a>
        </div>
        <p>@Niftiqet 2022 All Right Reserved</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "NifFooter"
}
</script>

<style lang="scss" scoped>
  .footer.container {
    background: transparent;
  }
</style>
