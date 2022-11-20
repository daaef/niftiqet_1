<template>
  <section>
    <header
      class="page--header events flex flex-col justify-center items-center"
    >
      <div class="container flex flex-col justify-center profile--view">
        <b-field class="file is-primary" :class="{ 'has-name': !!file }">
          <b-upload v-model="file" class="file-label">
            <button class="btn btn-outline border font-bold">
              <i class="isax isax-camera mr-2 text-xl"></i>
              Upload a Cover Photo
            </button>
            <span v-if="file" class="file-name">
              {{ file.name }}
            </span>
          </b-upload>
        </b-field>
      </div>
    </header>
    <main>
      <section class="home--body">
        <div class="cto--container container px-4 min-h-screen">
          <div class="profile--grid">
            <div class="profile--data">
              <div class="avatar--upload">
                <b-field>
                  <b-upload v-model="dropFiles" multiple drag-drop>
                    <section class="section">
                      <div class="content has-text-centered">
                        <button class="btn btn-outline border font-bold">
                          <i class="isax isax-camera mr-2 text-xl"></i>
                          Upload Avater
                        </button>
                      </div>
                    </section>
                  </b-upload>
                </b-field>
              </div>
              <div class="user--info text-center mt-4">
                <h3 class="text-xl">Sara Aniton</h3>
                <p class="text-primary text-lg font-bold">@Aniton</p>
                <p class="text-normal font-bold">Join March 2022</p>
                <div class="uk-tile theme-tile uk-padding-small items-center">
                  <p class="uk-h4 mr-6">
                    0x91a6dF52aA476378198422C922178560a5400E43
                  </p>
                  <i class="isax isax-copy"></i>
                </div>
              </div>
              <div class="profile--buttons">
                <button class="btn btn-outline border font-bold">
                  <i class="isax isax-edit mr-2 text-xl"></i>
                  Edit Profile
                </button>
              </div>
              <div class="grid mt-20 grid-flow-col gap-4">
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
              </div>
            </div>
            <div class="profile--views">
              <b-tabs v-model="activeTab" type="is-toggle">
                <b-tab-item label="Owned">
                  <event-card-grid :grid-size="2" />
                </b-tab-item>
                <b-tab-item label="Minted">
                  <event-card-grid :grid-size="2" />
                </b-tab-item>
                <b-tab-item label="Favorites">
                  <event-card-grid :grid-size="2" />
                </b-tab-item>
                <b-tab-item label="Following">
                  <user-card-grid :grid-size="3" />
                </b-tab-item>
                <b-tab-item label="Followers">
                  <user-card-grid :grid-size="3" />
                </b-tab-item>
              </b-tabs>
            </div>
          </div>
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
</style>
