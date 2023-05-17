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

<div class:mb-5={windowWidth <= 1035} class:pb-4={windowWidth <= 1035}>
  <div class="bottombar w-100 d-flex align-items-center">
    <div class="mx-auto text-center">
      <h3>Takip et!</h3>
      <p>
        Sosyal medya hesaplarımızdan bizi takip edin ve tüm etkinliklerimizden
        haberdar olun.
      </p>
      <div class="mx-auto redPartIcons d-flex justify-content-evenly">
        <button>
          <i class="fab fa-facebook-f fs-2" />
        </button>
        <button>
          <i class="fab fa-twitter fs-2" />
        </button>
        <button>
          <i class="fab fa-instagram fs-2" />
        </button>
        <button>
          <i class="fab fa-youtube fs-2" />
        </button>
        <button>
          <i class="fab fa-youtube fs-2" />
        </button>
      </div>
    </div>
  </div>
  <div class="mx-auto row lh-1 mt-5">
    <div class="col">
      <img src="/dijipin-logo.png" alt="Dijipin" class="dijipinLogo mx-auto" />
    </div>
    <!--1. Kısım - Dijipin-->
    <div class="col">
      <h5>Dijipin</h5>
      <div class="border border-danger mb-3 w-75" />
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>Hakkımızda</p>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>Oyunlar</p>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>Ödeme Yöntemleri</p>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>Hesap Numaraları</p>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>İletişim</p>
      </a>
    </div>
    <!--2. Kısım - Kurumsal-->
    <div class="col">
      <h5>Kurumsal</h5>
      <div class="border border-danger mb-3 w-75" />
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>Üyelik Sözleşmesi</p>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>Kullanım Koşulları</p>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>Gizlilik Politikası</p>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>Geri Ödeme Politikası</p>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <p>K.V.K.K.</p>
      </a>
    </div>
    <!--3. Kısım - Bize Ulaşın-->
    <div class="col">
      <h5>Bize Ulaşın</h5>
      <div class="border border-danger mb-3 w-75" />
      <a href="https://google.com/" class="text-decoration-none my-4">
        <div class="d-flex align-items-center">
          <i class="fas fa-phone-alt" />
          <p class="ms-2 my-auto">+90 535 345 47 46</p>
        </div>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <div class="d-flex align-items-center">
          <i class="fas fa-phone-alt" />
          <p class="ms-2 my-auto">info@dijipin.com</p>
        </div>
      </a>
      <a href="https://google.com/" class="text-decoration-none my-4">
        <div class="d-flex align-items-start">
          <i class="fas fa-phone-alt" />
          <div class="">
            <p class="ms-2 mb-1 my-auto">Beyazevler Mah.</p>
            <p class="ms-2 mb-1 my-auto">544 Sk. No.78</p>
            <p class="ms-2 my-auto">Gaziemir / İzmir / Türkiye</p>
          </div>
        </div>
      </a>
    </div>
  </div>
  <div class="border border-dark mb-3 w-100 opacity-25 mt-3" />
  <div class="w-100 d-flex align-items-center">
    <div class="lastBottom mx-auto text-center">
      <p class="text-center mb-0 mt-3">
        Copyright {new Date().getFullYear()} DİJİPİN | Sitemizdeki yazı, resim ve içeriklerin her
        hakkı saklıdır.
      </p>
    </div>
  </div>
</div>

<style lang="scss">
  .bottombar {
    background-color: #e71f5f;
    color: white;
    height: 220px;
  }

  .redPartIcons {
    max-width: 400px;

    button {
      background-color: transparent;
      color: white;
      border: 0;
      padding: 0;
      margin: 0;
    }
  }

  .dijipinLogo {
    max-width: 210px;
    max-height: 53px;
    display: flex;
  }

  a {
    color: black;
  }

  .row {
    max-width: 1200px;
  }

  .text-decoration-none {
    display: block;
    padding: 0;
    margin: 0;
    height: 10px;
  }

  .lastBottom {
    height: 80px;
  }
</style>
