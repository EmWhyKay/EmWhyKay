<script>
  import Siema from "siema";
  import { onMount, createEventDispatcher } from "svelte";

  export let perPage = 1;
  export let loop = true;
  export let autoplay = 0;
  export let duration = 300;
  export let easing = "ease-out";
  export let startIndex = 0;
  export let draggable = false;
  export let multipleDrag = true;
  export let dots = true;
  export let threshold = 20;
  export let rtl = false;
  export let controlButtons = true;
  let currentIndex = startIndex;

  let siema;
  let controller;
  let timer;
  const dispatch = createEventDispatcher();

  $: pips = controller ? controller.innerElements : [];
  $: currentPerPage = controller ? controller.perPage : perPage;
  $: totalDots = controller
    ? Math.ceil(controller.innerElements.length / currentPerPage)
    : [];

  onMount(() => {
    controller = new Siema({
      selector: siema,
      perPage: typeof perPage === "object" ? perPage : Number(perPage),
      loop,
      duration,
      easing,
      startIndex,
      draggable,
      multipleDrag,
      threshold,
      rtl,
      onChange: handleChange,
    });

    if (autoplay) {
      timer = setInterval(right, autoplay);
    }
    return () => {
      autoplay && clearInterval(timer);
      controller.destroy();
    };
  });

  export function isDotActive(currentIndex, dotIndex) {
    if (currentIndex < 0) currentIndex = pips.length + currentIndex;
    return (
      currentIndex >= dotIndex * currentPerPage &&
      currentIndex < dotIndex * currentPerPage + currentPerPage
    );
  }

  export function left() {
    controller.prev();
  }

  export function right() {
    controller.next();
  }

  export function go(index) {
    controller.goTo(index);
  }

  export function pause() {
    clearInterval(timer);
  }

  export function resume() {
    if (autoplay) {
      timer = setInterval(right, autoplay);
    }
  }

  function handleChange(event) {
    currentIndex = controller.currentSlide;
    dispatch("change", {
      currentSlide: controller.currentSlide,
      slideCount: controller.innerElements.length,
    });
  }

  function resetInterval(node, condition) {
    function handleReset(event) {
      pause();
      resume();
    }

    if (condition) {
      node.addEventListener("click", handleReset);
    }

    return {
      destroy() {
        node.removeEventListener("click", handleReset);
      },
    };
  }
</script>

<div class="carousel">
  <div class="slides" bind:this={siema}>
    <slot />
  </div>
  {#if dots}
    <ul>
      {#if controlButtons}
        <button
          class="my-auto"
          on:click={left}
          use:resetInterval={autoplay}
          aria-label="left"
        >
          <i class="fas fa-angle-left" />
        </button>
      {/if}

      {#each { length: totalDots } as _, i}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <li
          on:click={() => go(i * currentPerPage)}
          class={isDotActive(currentIndex, i) ? "active" : ""}
        />
      {/each}

      {#if controlButtons}
        <button
          class="my-auto"
          on:click={right}
          use:resetInterval={autoplay}
          aria-label="right"
        >
          <i class="fas fa-angle-right" />
        </button>
      {/if}
    </ul>
  {/if}
</div>

<style lang="scss">
  .carousel {
    position: relative;
    width: 100%;
    justify-content: center;
    align-items: center;
  }

  button {
    z-index: 50;
    border: none;
    background-color: transparent;

    i {
      font-size: 40px;
      color: rgba(0, 0, 0, 0.767);
    }
  }
  button:focus {
    outline: none;
  }
  ul {
    list-style-type: none;
    position: absolute;
    display: flex;
    justify-content: center;
    width: 100%;
    margin-top: -180px;
    padding: 0;
  }
  ul li {
    margin: 16px;
    border-radius: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    height: 20px;
    width: 20px;
    cursor: pointer;
  }
  ul li.active {
    background-color: rgba(0, 0, 0, 0.767);
  }
</style>
