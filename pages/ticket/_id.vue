<template>
  <div class="ticket--data sticky top-0">
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
            value="The Big Spring"
            class="input bg-base-100/10 w-full"
          />
        </div>
        <div class="form-control mt-2 w-full">
          <label class="label">
            <span class="label-text">Ticket Description</span>
          </label>
          <textarea disabled rows="3" class="textarea bg-base-100/10">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit.
          </textarea>
        </div>
        <div class="form-control mt-2 w-full">
          <label class="label">
            <span class="label-text">Created By</span>
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
            <span class="label-text">Owner</span>
          </label>
          <input
            type="text"
            disabled
            value="Obani.testnet"
            class="input bg-base-100/10 w-full"
          />
        </div>
        <div class="ticket--btns w-full mt-5">
          <NifBtn class="btn">Buy</NifBtn>
          <button class="btn">Sell</button>
          <div class="ticket--btn flex mt-5 w-full justify-center">
            <button class="btn btn-success text-white">Transfer</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.ticket--btns {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  .btn {
    width: calc(50% - 10px);
    text-transform: none;
  }
  .ticket--btn {
  }
}
</style>
