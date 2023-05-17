<script>
  import "../app.scss";
  import Sidebar from "../components/sidebar.svelte";
  import Header from "../components/header.svelte";
  import BottomBar from "../components/bottombar.svelte";
  import MobileBottomBar from "../components/mobile-bottombar.svelte";
  import { onMount } from "svelte";

  let show = false;
  let windowWidth = 1100;

  onMount(() => {
    windowWidth = window.innerWidth;
    window.addEventListener("resize", () => {
      windowWidth = window.innerWidth;
    });
  });
</script>

<svelte:head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap"
    rel="stylesheet"
  />
</svelte:head>

{#if windowWidth > 1035}
  <Sidebar bind:show />
{/if}

<div class="content" class:navbar-left={windowWidth > 1035}>
  <Header />
  <main>
    <slot />
  </main>

  <footer class="d-flex align-items-center justify-content-center">
    <p />
  </footer>

  <BottomBar />

  {#if windowWidth <= 1035}
    <MobileBottomBar />
  {/if}
</div>

<div class="overlay" style={show ? "display: block;" : "display: none;"} />

<style lang="scss">
  .content {
    flex: 1;
    transition: all 0.3s ease;
    position: relative;
  }

  .navbar-left {
    margin-left: 80px;
  }

  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 999;
    display: none;
  }
</style>
