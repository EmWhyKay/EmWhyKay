<script>
  export let show = false;
  let showText = false;

  function delay(time) {
    return new Promise((resolve) => setTimeout(resolve, time));
  }

  async function toggle() {
    show = !show;
    if (showText == true) showText = false;
    else {
      await delay(150);
      showText = true;
    }
  }
</script>

<div class="sidebarMenu position-fixed shadow top-0 left-0 bg-white" class:open={show}>
  <div>
    <button class="sidebarButton" on:click={() => toggle()}>
      <i class="fas fa-bars" />
    </button>

    <img src="/dijipin-logo.png" alt="dijipin" class="logo mt-3" />
  </div>

  <div class="d-flex flex-column mt-4">
    <ul>
      <button
        on:click={() => {
          toggle();
          window.location.href = "/";
        }}
      >
        <div>
          <i class="fas fa-home" />
          {#if showText}
            <span>Ana Sayfa</span>
          {/if}
        </div>
      </button>
      <button
        on:click={() => {
          toggle();
          window.location.href = "/";
        }}
      >
        <div>
          <i class="fas fa-gamepad" />
          {#if showText}
            <span>Oyunlar</span>
          {/if}
        </div>
      </button>
      <button
        on:click={() => {
          toggle();
          window.location.href = "/";
        }}
      >
        <div>
          <i class="fas fa-file-alt" />
          {#if showText}
            <span>Haberler</span>
          {/if}
        </div>
      </button>
      <button
        on:click={() => {
          toggle();
          window.location.href = "/";
        }}
      >
        <div>
          <i class="fas fa-money-bill" />
          {#if showText}
            <span>Bakiye Yükle</span>
          {/if}
        </div>
      </button>
      <button
        on:click={() => {
          toggle();
          window.location.href = "/";
        }}
      >
        <div>
          <i class="fas fa-shopping-cart" />
          {#if showText}
            <span>Siparişlerim</span>
          {/if}
        </div>
      </button>
    </ul>
  </div>
</div>

<style lang="scss">
  .sidebarMenu {
    z-index: 999999;
    height: 100%;
    width: 80px;
    transition: all 0.5s ease;
  }

  .open {
    width: 325px;
  }

  .sidebarButton {
    position: absolute;
    background-color: transparent;
    border: 0;
    padding: 0;
    margin-top: 1.8rem;
    margin-left: 1.8rem;
  }

  .fas {
    font-size: 25px;
    color: #000;
  }

  ul {
    padding: 0;
    margin: 0;
    list-style: none;

    button {
      background-color: transparent;
      border: 0;
      padding: 0;
      margin: 0;
      width: 100%;
      height: 55px;
      padding-left: 1.5rem;
      display: flex;
      align-items: center;
      justify-content: flex-start;

      div {
        width: 35px;
        display: flex;
        align-items: center;
        justify-content: center;
      }

      span {
        position: absolute;
        left: 85px;
      }

      &:hover {
        background-color: #fde8ef;
      }

      &:hover i {
        color: #ea1e5f;
      }
    }
  }

  .logo {
    width: 198px;
    height: 50px;
    margin-left: 6.5rem;
  }
</style>
