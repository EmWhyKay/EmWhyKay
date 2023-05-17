<script>
  import { onMount } from "svelte";
  import { afterUpdate } from "svelte";

  let windowWidth = 1100;

  onMount(() => {
    windowWidth = window.innerWidth;
    window.addEventListener("resize", () => {
      windowWidth = window.innerWidth;
    });
  });

  afterUpdate(() => {
    const cardGroup = document.getElementById("card-group");
    cardGroup.scrollLeft = 0;
  });
</script>

<!--Popüler Oyunlar-->
<div class:mx-5={windowWidth > 1035} class:mx-2={windowWidth <= 1035}>
  <div class="d-flex mb-3">
    <h3>Popüler Oyunlar</h3>
    <button class="btn ms-2">
      Tüm Oyunları Gör
      <i class="fas fa-chevron-right" />
    </button>
  </div>

  <!--Popüler Oyunlar - Kartlar-->
  <div id="card-group" class="card-group d-flex justify-content-between">
    <div class="card me-3">
      <img
        src="/valorant-populer.jpg"
        class="card-img-top px-3 pt-3"
        alt="Popüler Oyun"
      />
      <div class="card-body">
        <!--Popüler Oyunlar - Oyun İsmi-->
        <h5 class="card-title">Valorant</h5>
        <!--Popüler Oyunlar - Firma İsmi-->
        <p class="card-text position-absolute bottom-0 mb-2 pb-1">Riot Games</p>
        <!--Popüler Oyunlar - Desteklenen Yerler (list ile kullanılabilir ?)-->
        <div class="position-absolute end-0 bottom-0 mb-2 pb-1 me-3">
          <i class="fas fa-desktop" />
        </div>
      </div>
    </div>

    <div class="card me-3">
      <img
        src="/mlegends-populer.jpg"
        class="card-img-top px-3 pt-3"
        alt="Popüler Oyun"
      />
      <div class="card-body">
        <!--Popüler Oyunlar - Oyun İsmi-->
        <h5 class="card-title">Mobile Legends: Bang Bang</h5>
        <!--Popüler Oyunlar - Firma İsmi-->
        <p class="card-text position-absolute bottom-0 mb-2 pb-1">Moonton</p>
        <!--Popüler Oyunlar - Desteklenen Yerler (list ile kullanılabilir ?)-->
        <div class="position-absolute end-0 bottom-0 mb-2 pb-1 me-3">
          <i class="fas fa-desktop" />
        </div>
      </div>
    </div>

    <div class="card me-3">
      <img
        src="/googleplay-populer.jpg"
        class="card-img-top px-3 pt-3"
        alt="Popüler Oyun"
      />
      <div class="card-body">
        <!--Popüler Oyunlar - Oyun İsmi-->
        <h5 class="card-title">Google Play Cüzdan Kodu</h5>
        <!--Popüler Oyunlar - Firma İsmi-->
        <p class="card-text position-absolute bottom-0 mb-2 pb-1">Google</p>
        <!--Popüler Oyunlar - Desteklenen Yerler (list ile kullanılabilir ?)-->
        <div class="position-absolute end-0 bottom-0 mb-2 pb-1 me-3">
          <i class="fas fa-desktop" />
        </div>
      </div>
    </div>

    <div class="card me-3">
      <img
        src="/appstore-populer.jpg"
        class="card-img-top px-3 pt-3"
        alt="Popüler Oyun"
      />
      <div class="card-body">
        <!--Popüler Oyunlar - Oyun İsmi-->
        <h5 class="card-title">iTunes Hediye Kartı</h5>
        <!--Popüler Oyunlar - Firma İsmi-->
        <p class="card-text position-absolute bottom-0 mb-2 pb-1">Apple</p>
        <!--Popüler Oyunlar - Desteklenen Yerler (list ile kullanılabilir ?)-->
        <div class="position-absolute end-0 bottom-0 mb-2 pb-1 me-3">
          <i class="fas fa-desktop" />
        </div>
      </div>
    </div>

    <div class="card">
      <img
        src="/geforcen-populer.jpg"
        class="card-img-top px-3 pt-3"
        alt="Popüler Oyun"
      />
      <div class="card-body">
        <!--Popüler Oyunlar - Oyun İsmi-->
        <h5 class="card-title">GeForce Now Game Plus</h5>
        <!--Popüler Oyunlar - Firma İsmi-->
        <p class="card-text position-absolute bottom-0 mb-2 pb-1">Nvidia</p>
        <!--Popüler Oyunlar - Desteklenen Yerler (list ile kullanılabilir ?)-->
        <div class="position-absolute end-0 bottom-0 mb-2 pb-1 me-3">
          <i class="fas fa-desktop" />
        </div>
      </div>
    </div>
  </div>
</div>

<style lang="scss">
  .btn {
    color: #e71f5f;
    border: 0;

    &:hover {
      text-decoration: underline;
      color: #e71f5f;
    }

    &:focus {
      color: #e71f5f;
    }
  }

  #card-group {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
  }

  .card {
    border-radius: 10px !important;
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.2);
    height: 18rem;
    flex: 0 0 auto;
  }

  .card-text {
    font-size: 13px;
  }
</style>
