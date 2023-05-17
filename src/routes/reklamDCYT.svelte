<script>
  import { onMount } from "svelte";

  let windowWidth = 1100;

  onMount(() => {
    windowWidth = window.innerWidth;
    window.addEventListener("resize", () => {
      windowWidth = window.innerWidth;
    });
  });
</script>

<div class="container-fluid mb-5">
  <div class="row">
    <div class="col">
      <div class="image-container">
        <div class="image-item" class:px-2={windowWidth > 767}>
          <img
            src="/discord-banner.jpg"
            alt="Dijipin Discord"
            class="img-fluid"
          />
        </div>
        <div class="image-item" class:px-2={windowWidth > 767}>
          <img
            src="/youtube-banner.jpg"
            alt="Dijipin Youtube"
            class="img-fluid"
          />
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .image-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
  }

  .image-item {
    flex: 0 0 50%; /* Yarı genişlikte */
    box-sizing: border-box;
    text-align: center;
    margin-bottom: 10px; /* İsteğe bağlı boşluk ayarı */
  }

  .image-item img {
    max-width: 100%;
    max-height: 100%;
    width: 100%;
    height: auto; /* Değişiklik */
    object-fit: contain;
  }

  @media (max-width: 767px) {
    /* Mobil ekran boyutları için özelleştirme */
    .image-item {
      flex: 0 0 100%; /* Tam genişlikte */
    }
  }
</style>
