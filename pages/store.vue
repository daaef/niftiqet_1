<template>
  <section>
    <header
      class="page--header store flex flex-col justify-center items-center"
    >
      <div class="container flex flex-col justify-center">
        <h4>Store</h4>
        <div class="text-sm breadcrumbs">
          <ul>
            <li><nuxt-link to="/">Home</nuxt-link></li>
            <li class="text-primary">Store</li>
          </ul>
        </div>
      </div>
      <div class="flex flex-col bg--shape justify-center">
        <div class="container">
          <div class="user--avatar">
            <div class="w-25 rounded-full overflow-hidden">
              <img src="https://placeimg.com/192/192/people" />
            </div>
          </div>
          <div class="store--stats">
            <h3 class="font-bold text--badge">
              ehapa.Niftiqet.testnet
              <span class="logo-badge"
                ><img src="/logo-badge.png" alt="LOGO Badge"
              /></span>
            </h3>
            <div class="stats--grid">
              <div class="stat">
                <h3>Total ticket Minted</h3>
                <p class="font-bold">30</p>
              </div>
              <div class="stat">
                <h3>Total Owners</h3>
                <p class="font-bold">30</p>
              </div>
              <div class="stat">
                <h3>Total ticket Minted</h3>
                <p class="font-bold">30</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </header>
    <main>
      <section class="home--body">
        <div class="store--tabs">
          <b-tabs type="is-toggle" position="is-centered">
            <b-tab-item label="My Tickets">
              <div class="cto--container container px-4 min-h-screen">
                <div class="flex justify-between">
                  <h2 class="text-3xl font-bold">My Tickets</h2>
                  <nif-btn>Contract</nif-btn>
                </div>
                <event-card-grid />
                <div class="flex pagination justify-center mt-16">
                  <div class="btn-group">
                    <button class="btn">Previous</button>
                    <button class="btn">1</button>
                    <button class="btn">2</button>
                    <button class="btn">3</button>
                    <button class="btn">Next</button>
                  </div>
                </div>
              </div>
            </b-tab-item>
            <b-tab-item label="Minters">
              <div class="cto--container container px-4 min-h-screen">
                <div class="profile--grid">
                  <div class="profile--data">
                    <div class="card">
                      <div class="card-body flex flex-col">
                        <h2 class="card-title">Store Setting</h2>
                        <div class="divider my-3"></div>
                        <b-field label="Minted Ticket">
                          <b-select placeholder="Select a Ticket">
                            <option value="1">ehapa.Niftiqet.testnet</option>
                          </b-select>
                        </b-field>
                        <nuxt-link to="/store">View Store</nuxt-link>
                        <nuxt-link to="/settings">Store Settings</nuxt-link>
                        <div class="flex justify-center w-full mt-6">
                          <nif-btn>Mint NFT Ticket</nif-btn>
                        </div>
                        <div class="divider my-3"></div>
                        <a href="#" class="text-primary text-2xl">New Store</a>
                      </div>
                    </div>
                  </div>
                  <div class="profile--views">
                    <div
                      tabindex="0"
                      class="collapse rounded-2xl bg-base-100/30 collapse-arrow"
                    >
                      <input type="checkbox" checked />
                      <div class="collapse-title text-sm font-bold">
                        Basic Information
                      </div>
                      <div class="collapse-content">
                        <div class="form-control w-full">
                          <label class="label">
                            <span class="label-text">Name of Store</span>
                          </label>
                          <input
                            type="text"
                            disabled
                            value="Radium Animated Monster"
                            class="input bg-base-100/10 w-full"
                          />
                        </div>
                        <div class="form-control mt-2 w-full">
                          <label class="label">
                            <span class="label-text">Store Description</span>
                          </label>
                          <textarea
                            disabled
                            rows="4"
                            class="textarea bg-base-100/10"
                          >
                      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Dolor porta ut neque maecenas egestas ornare habitasse amet pellentesque. Lorem libero volutpat augue augue vitae. Elementum et tempor gravida metus, est ut. At amet, nibh platea luctus molestie volutpat risus.
                    </textarea
                          >
                        </div>
                        <div class="grid grid-cols-2 gap-4">
                          <div class="form-control mt-2 w-full">
                            <label class="label">
                              <span class="label-text">Website URL</span>
                            </label>
                            <input
                              type="text"
                              disabled
                              value="near.Niftiqet.testnet"
                              class="input bg-base-100/10 w-full"
                            />
                          </div>
                          <div class="form-control mt-2 w-full">
                            <label class="label">
                              <span class="label-text">Community URL</span>
                            </label>
                            <input
                              type="text"
                              disabled
                              value="Obani.testnet"
                              class="input bg-base-100/10 w-full"
                            />
                          </div>
                          <div class="form-control mt-2 w-full">
                            <label class="label">
                              <span class="label-text">Twitter URL</span>
                            </label>
                            <input
                              type="text"
                              disabled
                              value="ehapa.Niftiqet.testnet"
                              class="input bg-base-100/10 w-full"
                            />
                          </div>
                          <div class="form-control mt-2 w-full">
                            <label class="label">
                              <span class="label-text">Instagram URL</span>
                            </label>
                            <input
                              type="text"
                              disabled
                              value="ehapa.Niftiqet.testnet"
                              class="input bg-base-100/10 w-full"
                            />
                          </div>
                          <div class="form-control mt-2 w-full">
                            <label class="label">
                              <span class="label-text">Facebook URL</span>
                            </label>
                            <input
                              type="text"
                              disabled
                              value="ehapa.Niftiqet.testnet"
                              class="input bg-base-100/10 w-full"
                            />
                          </div>
                          <div class="form-control mt-2 w-full">
                            <label class="label">
                              <span class="label-text">Whatsapp URL</span>
                            </label>
                            <input
                              type="text"
                              disabled
                              value="ehapa.Niftiqet.testnet"
                              class="input bg-base-100/10 w-full"
                            />
                          </div>
                        </div>
                      </div>
                    </div>
                    <div
                      tabindex="0"
                      class="collapse mt-4 rounded-2xl bg-base-100/30 collapse-arrow"
                    >
                      <input type="checkbox" checked />
                      <div class="collapse-title text-sm font-bold">
                        Minters
                      </div>
                      <div class="collapse-content">
                        <div class="form-control w-full">
                          <label class="label">
                            <span class="label-text">Name of Store</span>
                          </label>
                          <input
                            type="text"
                            disabled
                            value="Radium Animated Monster"
                            class="input bg-base-100/10 w-full"
                          />
                        </div>
                        <div class="form-control mt-2 w-full">
                          <label class="label">
                            <span class="label-text">Store Description</span>
                          </label>
                          <textarea
                            disabled
                            rows="4"
                            class="textarea bg-base-100/10"
                          >
                      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Dolor porta ut neque maecenas egestas ornare habitasse amet pellentesque. Lorem libero volutpat augue augue vitae. Elementum et tempor gravida metus, est ut. At amet, nibh platea luctus molestie volutpat risus.
                    </textarea
                          >
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </b-tab-item>
          </b-tabs>
        </div>
      </section>
    </main>
  </section>
</template>

<script>
export default {
  data() {
    return {
      activeTab: 0,
      dropFiles: [],
      file: null,
    }
  },
  methods: {
    deleteDropFile(index) {
      this.dropFiles.splice(index, 1)
    },
  },
}
</script>

<style lang="scss">
.home--body {
  .container {
    .profile--grid {
      .event--card-grid {
        margin-top: 20px;
      }
    }
  }
}
.profile--views {
  .b-tabs {
    nav {
      background: transparent !important;
    }
    [role='tablist'] {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      grid-gap: 20px;
      & > li {
        a {
          border-radius: 8px;
          border-color: var(--bc);
          &:hover {
            background: linear-gradient(to right, #27a0af, #4680bd);
            border: none;
            span {
              color: #fafafa;
            }
          }
        }
        &.is-active {
          a {
            background: linear-gradient(to right, #27a0af, #4680bd);
            border: none;
            span {
              color: #fafafa;
            }
          }
        }
      }
    }
  }
}
.btn--grid {
  grid-template-columns: repeat(5, 1fr);
  grid-gap: 20px;
}
.profile--buttons {
  margin-top: 60px;
  text-align: center;
}
.theme-tile {
  margin-top: 40px;
  background: hsl(var(--b1) / 0.3);
  border-radius: 12px;
  display: flex;
  justify-content: space-between;
}
.profile--view {
  input {
    opacity: 0;
    &:hover {
      & ~ .image--uploader {
        .btn {
          background: #fafafa;
          color: #2a4d72;
        }
      }
    }
  }
  /*.image--uploader {
    position: relative;
    z-index: 3;
  }*/
}
.pagination {
  .btn {
    background: hsla(var(--b1) / 0.4);
    backdrop-filter: blur(5px);
    color: hsla(var(--bc) / 0.9);
  }
}
.avatar--upload {
  min-height: 300px;
  .upload {
    background: #294b59;
    border-radius: 13.353px;
    .upload-draggable {
      border-width: 0;
    }
  }
}
.profile--grid {
  display: grid;
  grid-gap: 20px;
  grid-template-columns: 1.3fr 2.3fr;
  .upload {
    min-height: 300px;
    .upload-draggable {
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
  .profile {
    margin-top: 60px;
    .formkit-wrapper {
      max-width: 100%;
    }
    .file--input {
      position: relative;
      height: 300px;
      text-align: center;
      width: 100%;
    }
    input {
      background: hsl(var(--b1) / 0.2);
      border-radius: 13.353px;
      border: none;
      &:hover {
        & ~ .image--uploader {
          .btn {
            background: #fafafa;
            color: #2a4d72;
          }
        }
      }
    }
    .image--uploader {
      position: relative;
      //z-index: 3;
      display: inline-block;
      height: unset;
      top: 50%;
      transform: translateY(-50%);
      button {
        text-transform: none;
      }
    }
  }
}

.store--tabs {
  width: 100%;
  .tabs {
    padding: 25px 30px;
    background: hsla(var(--s) / 0.7);
    width: 100%;
    ul {
      display: grid;
      grid-gap: 25px;
      grid-template-columns: auto auto auto auto;
      width: 100%;
      li {
        a {
          border-radius: 8px !important;
          transition: 0.3s ease-in-out;
          &:hover,
          &:active,
          &:focus {
            background: hsl(var(--p)) !important;
            color: hsl(var(--bc)) !important;
          }
        }
        &.is-active {
          a {
            border-width: 0;
            background: hsl(var(--p)) !important;
            color: hsl(var(--bc));
          }
        }
      }
    }
  }
}
</style>
