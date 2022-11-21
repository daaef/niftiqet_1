<template>
  <nav
    class="sticky top-0 w-full transition-colors my-navigation backdrop-blur-md bg-base-100/10"
  >
    <div class="container px-4 navbar">
      <div class="navbar-start">
        <div class="dropdown">
          <label tabindex="0" class="btn btn-ghost lg:hidden">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-5 h-5"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h8m-8 6h16"
              />
            </svg>
          </label>
          <ul
            tabindex="0"
            class="p-2 mt-3 shadow menu dropdown-content rounded-box w-52"
          >
            <li><a>Marketplace</a></li>
            <li tabindex="0">
              <a class="justify-between">
                Resources
                <svg
                  class="fill-current"
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                >
                  <path
                    d="M8.59,16.58L13.17,12L8.59,7.41L10,6L16,12L10,18L8.59,16.58Z"
                  />
                </svg>
              </a>
              <ul class="p-2">
                <li>
                  <a><i class="isax isax-profile-2user"></i> About Us</a>
                </li>
                <li>
                  <a><i class="isax isax-call"></i> Contact Us</a>
                </li>
                <li>
                  <a><i class="isax isax-arrow"></i> Royalties</a>
                </li>
                <li>
                  <nuxt-link to="/collections">
                    <i class="isax isax-element-equal"></i>
                    Collections
                  </nuxt-link>
                </li>
                <li>
                  <a><i class="isax isax-info-circle"></i> Blog</a>
                </li>
              </ul>
            </li>
            <li><a>Create</a></li>
          </ul>
        </div>
        <nuxt-link to="/" class="text-xl normal-case btn btn-ghost logo--link">
          <img src="/logo.png" class="logo--light" alt="" />
          <img src="/logo-dark.png" class="logo--dark" alt="" />
        </nuxt-link>
      </div>
      <div class="hidden navbar-center lg:flex">
        <ul class="p-0 menu menu-horizontal">
          <li>
            <nuxt-link class="font-bold uppercase" to="/mint">Create</nuxt-link>
          </li>
          <li>
            <nuxt-link class="font-bold uppercase" to="/events"
              >Events</nuxt-link
            >
          </li>
          <li>
            <nuxt-link to="/about" class="font-bold uppercase">About</nuxt-link>
          </li>
          <li tabindex="0">
            <a class="font-bold uppercase">
              More
              <svg
                class="fill-current"
                xmlns="http://www.w3.org/2000/svg"
                width="20"
                height="20"
                viewBox="0 0 24 24"
              >
                <path
                  d="M7.41,8.58L12,13.17L16.59,8.58L18,10L12,16L6,10L7.41,8.58Z"
                />
              </svg>
            </a>
            <ul class="p-2">
              <li>
                <a><i class="isax isax-profile-2user"></i> About Us</a>
              </li>
              <li>
                <a><i class="isax isax-call"></i> Contact Us</a>
              </li>
              <li>
                <a><i class="isax isax-arrow"></i> Royalties</a>
              </li>
              <li>
                <nuxt-link to="/collections"
                  ><i class="isax isax-element-equal"></i>
                  Collections</nuxt-link
                >
              </li>
              <li>
                <a><i class="isax isax-info-circle"></i> Blog</a>
              </li>
            </ul>
          </li>
        </ul>
      </div>
      <div class="navbar-end">
        <button class="btn btn-ghost btn-circle">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-5 h-5"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
            />
          </svg>
        </button>
        <!--    <nif-btn @click.prevent="wallety?.connect({ requestSignIn: true })">
          <i class="mr-2 cf cf-near"></i> NEAR Login
        </nif-btn>-->
        <div v-if="isConnected" class="user--details">
          <h3>{{ details.accountId }}</h3>
          <p>{{ details.balance }}N</p>
        </div>
        <div v-if="isConnected" class="dropdown dropdown-end">
          <label
            tabindex="0"
            class="p-0 rounded-full btn btn-ghost rounded-btn"
          >
            <div class="avatar">
              <div class="w-8 rounded-full">
                <img src="https://placeimg.com/192/192/people" alt="" />
              </div>
            </div>
          </label>
          <ul
            tabindex="0"
            class="p-2 mt-4 shadow menu dropdown-content bg-base-100 rounded-box w-52"
          >
            <li><nuxt-link to="/profile">Profile</nuxt-link></li>
            <li v-if="userType === 'Buyer'">
              <nuxt-link to="/profile">Sell Tickets</nuxt-link>
            </li>
            <li v-else><nuxt-link to="/profile">Buy Tickets</nuxt-link></li>
            <li><nuxt-link to="/activity">Activity</nuxt-link></li>
            <li><nuxt-link to="/settings">Settings</nuxt-link></li>
            <li><a @click="disconnectWallet">Logout</a></li>
          </ul>
        </div>
        <a
          v-if="!isConnected"
          class="capitalize btn def--btn"
          @click.prevent="openLogin = true"
        >
          <i class="mr-2 cf cf-near"></i> NEAR Login
        </a>
      </div>
    </div>
    <div
      v-if="openLogin"
      class="my--modal"
      :class="openLogin ? 'active--modal' : ''"
    >
      <div class="relative my-modal--content">
        <a href="#" @click="openLogin = false"
          ><b-icon class="absolute close-icon" icon="close" type="is-white"
        /></a>
        <h3 class="w-full mb-5 text-2xl font-bold text-center text-white">
          Login to Niftiqet
        </h3>
        <div class="user-type--picker">
          <b-field>
            <b-radio-button v-model="userType" native-value="Creator">
              <span>EVENT CREATOR</span>
            </b-radio-button>

            <b-radio-button v-model="userType" native-value="Buyer">
              <span>BUYER</span>
            </b-radio-button>
          </b-field>
        </div>
        <button
          class="w-full mt-6 capitalize btn def--btn"
          @click.prevent="login()"
        >
          Continue to NEAR Wallet
        </button>
      </div>
    </div>
  </nav>
</template>
<script>
import { mapWritableState } from 'pinia'
import { useStore } from '@/store'

export default {
  name: 'NavBar',
  setup() {
    const store = useStore()

    return { store }
  },
  data() {
    return {
      checking: 'home',
      on: this.$colorMode.preference === 'dark',
      openLogin: false,
    }
  },
  computed: {
    address() {
      return location.origin
    },
    ...mapWritableState(useStore, [
      'userType',
      'wallet',
      'details',
      'isConnected',
      'loading',
    ]),
  },
  watch: {
    userType(newVal) {
      localStorage.setItem('userType', newVal)
      sessionStorage.setItem('userType', newVal)
    },
  },
  mounted() {
    if (
      localStorage.getItem('theme') !== 'dark' &&
      localStorage.getItem('theme') !== 'light'
    ) {
      localStorage.setItem('theme', 'dark')
    }
    const themeSaved = localStorage.getItem('theme')
    let theme = themeSaved

    if (themeSaved === 'dark') {
      theme = 'dark'
    } else if (themeSaved === 'light') {
      theme = 'light'
    }

    document.documentElement.setAttribute('data-theme', theme)
  },
  methods: {
    async login() {
      console.log('login in')
      await this.wallet?.connect({ requestSignIn: true })
      // await this.wallet.activeWallet.requestSignIn({
      //   successUrl: `${this.address}/${
      //     this.userType === 'Buyer' ? 'events' : 'mint'
      //   }`,
      //   failureUrl: `${this.address}`,
      // })
    },
    async disconnectWallet() {
      await this.store?.wallet?.disconnect()
      await this.store?.setupWallet()
    },
    toggleTheme() {
      const savedTheme = document.documentElement.getAttribute('data-theme')
      let chosenTheme = ''

      if (savedTheme === 'dark') {
        chosenTheme = 'light'
      } else {
        chosenTheme = 'dark'
      }

      document.documentElement.setAttribute('data-theme', chosenTheme)
      localStorage.setItem('theme', chosenTheme)
    },
  },
}
</script>
<style lang="scss">
.my-navigation {
  z-index: 30;
  position: fixed;
}
.my--modal {
  height: 100vh;
  width: 100%;
  z-index: 300;
  background: rgba(0, 0, 0, 0.3);
  position: fixed;
  backdrop-filter: blur(300px);
  top: 0;
  left: 0;
  justify-content: center;
  align-items: center;
  transition: 0.3s ease-in-out;
  opacity: 0;
  display: none;
  &.active--modal {
    display: flex;
    opacity: 1;
  }
  .my-modal--content {
    background: #1d2c39;
    border-radius: 24px;
    padding: 30px;
    .close-icon {
      right: 30px;
    }
    .user-type--picker {
      background: #f2fafc;
      border-radius: 16px;
      padding: 15px 30px;
      .field.has-addons {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
        label {
          border: 0 !important;
          box-shadow: none !important;
          outline: none !important;
          background: transparent;
          &.is-selected {
            background: #0095c2;
            border-radius: 12px;
            position: relative;
            span {
              color: #fbffff;
              position: relative;
            }
            &:before {
              content: '';
              position: absolute;
              background: #0095c2;
              width: calc(100% + 4px);
              height: calc(100% + 4px);
              left: -2px;
              top: -2px;
              border-radius: 12px;
            }
            &:after {
              content: '';
              position: absolute;
              background: transparent;
              width: 100%;
              height: 100%;
              left: 0;
              top: 0;
              border-radius: 12px;
              border: 2px solid #fbffff;
            }
          }
          span {
            color: #0095c2;
            font-weight: bold;
          }
          &:hover {
          }
        }
      }
    }
  }
}
</style>
