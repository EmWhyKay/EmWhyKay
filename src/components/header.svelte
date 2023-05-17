<script>
  import { onMount } from "svelte";
  let windowWidth = 0;

  onMount(() => {
    windowWidth = window.innerWidth;
    window.addEventListener("resize", () => {
      windowWidth = window.innerWidth;
    });
  });
</script>

<div class="header position-fixed top-0 align-items-center bg-white">
  <div class="logoEmpty" />

  {#if windowWidth > 1035}
    <div class="searchbar">
      <i class="fa fa-search opacity-75" />
      <input type="text" placeholder="Arama" class="border-0" />
    </div>
  {/if}

  <div class="rightPart">
    {#if windowWidth > 1035}
      <button>
        <i class="fa fa-moon opacity-75" />
      </button>
      <div class="border border-dark mx-3 opacity-25" />
    {/if}
    <button>
      <i class="fa fa-bell opacity-75" />
    </button>
    <div class="border border-dark mx-3 opacity-25" />
    <button>
      <i class="fa fa-shopping-basket opacity-75" />
    </button>
    <div class="border border-dark mx-3 opacity-25" />
    {#if windowWidth > 1035}
      <button>
        <img src="/tr-icon.svg" alt="tr-icon" />
      </button>
      <div class="border border-dark mx-3 opacity-25" />
    {/if}
    <button
      class="
    d-flex
    align-items-center
    justify-content-center
    "
    >
      Giriş Yap
      <i class="fa fa-user-circle opacity-75 ms-2" />
    </button>
  </div>
</div>

<style lang="scss">
  .header {
    display: fixed;
    top: 0;
    z-index: 999;
    width: 96%;
    background-color: white;
    height: 100px;
    display: flex;
  }

  .logoEmpty {
    width: 198px;
    height: 50px;
    margin-left: 1.5rem;
    margin-bottom: 1.1rem;
    background-color: transparent;
  }

  .searchbar {
    margin-bottom: 10px;
    margin-left: 50px;
    padding-left: 15px;
    border: 1px solid #a8a8a8;
    border-radius: 7px;
    width: 350px;

    input {
      border: 0;
      padding: 0;
      margin: 0;
      height: 35px;
      width: 300px;
      border-radius: 25px;
      padding-left: 0.3rem;
      outline: none;
    }
  }

  .rightPart {
    margin-left: auto;
    margin-right: 2.6rem;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    justify-content: center;

    button {
      background-color: transparent;
      border: 0;
      padding: 0;

      i {
        font-size: 22px;
      }

      img {
        width: 22px;
        height: 22px;
      }
    }

    .border {
      height: 35px;
    }
  }
</style>
