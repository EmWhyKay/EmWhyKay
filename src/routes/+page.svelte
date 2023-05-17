<script>
  import Carousel from "../components/carousel.svelte";
  import PopulerOyunlar from "./populerOyunlar.svelte";
  import ReklamDCYT from "./reklamDCYT.svelte";
  import { onMount } from "svelte";

  let windowWidth = 0;

  onMount(() => {
    windowWidth = window.innerWidth;
    window.addEventListener("resize", () => {
      windowWidth = window.innerWidth;
    });
  });

  let images = [
    "/slider.jpg",
    "/slider.jpg",
    "/slider.jpg",
    "/slider.jpg",
    "/slider.jpg",
    "/slider.jpg",
  ];

  let cards = [
    "/valorant-card.jpg",
    "/pubg-card.jpg",
    "/steam-card.jpg",
    "/lol-card.jpg",
    "/pashafencer-card.jpg",
  ];
</script>

<div>
  <!--Carousel-->
  <Carousel
    autoplay="5000"
    controlButtons={windowWidth > 1035 ? true : false}
    dots={windowWidth > 1035 ? true : false}
  >
    {#each images as image, index (index)}
      <img src={image} alt="slider" class="slider" />
    {/each}
  </Carousel>

  <!--Carousel'in altındaki görseller-->
  {#if windowWidth > 1035}
    <div
      class="cards mx-5 d-flex justify-content-center align-items-center justify-content-between"
    >
      {#each cards as card, index (index)}
        <button class="mx-1">
          <img src={card} alt="card" />
        </button>
      {/each}
    </div>
  {/if}

  <ReklamDCYT />

  <PopulerOyunlar />
</div>

<style lang="scss">
  .slider {
    width: 100%;
    height: 100%;
    object-fit: cover;
    margin-top: 100px;
  }

  .cards {
    position: relative;
    top: -110px;
  }

  button {
    background-color: transparent;
    border: 0;
    padding: 0;
    margin: 0;

    img {
      border-radius: 10px;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  @media (max-width: 1035px) {
    .cards {
      position: static;
      margin-top: 20px;
    }
  }
</style>
