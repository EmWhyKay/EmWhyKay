<script>
  import { onMount } from "svelte";
  var currentPage = "anasayfa";

  onMount(() => {
    var buttons = document.querySelectorAll(".btn");

    buttons.forEach(function (button) {
      var targetPage = button.dataset.page;

      if (currentPage === targetPage) {
        button.classList.add("btn-primary");
      }
    });
  });

  function changePage(targetPage) {
    if (currentPage !== targetPage) {
      currentPage = targetPage;

      var buttons = document.querySelectorAll(".btn");

      buttons.forEach(function (btn) {
        if (btn.dataset.page === targetPage) {
          btn.classList.add("btn-primary");
        } else {
          btn.classList.remove("btn-primary");
        }
      });
    }
  }
</script>

<div class="fixed-bottom w-100 d-flex align-items-center">
  <div class="container">
    <div class="row">
      <div class="col-3 g-0">
        <button
          class="btn border-0 rounded-0 w-100"
          data-page="anasayfa"
          on:click={() => changePage("anasayfa")}
        >
          <i class="fas fa-home fs-2" />
        </button>
      </div>
      <div class="col-3 g-0">
        <button
          class="btn border-0 rounded-0 w-100"
          data-page="oyunlar"
          on:click={() => changePage("oyunlar")}
        >
          <i class="fas fa-gamepad fs-2" />
        </button>
      </div>
      <div class="col-3 g-0">
        <button
          class="btn border-0 rounded-0 w-100"
          data-page="haberler"
          on:click={() => changePage("haberler")}
        >
          <i class="fas fa-file-alt fs-2" />
        </button>
      </div>
      <div class="col-3 g-0">
        <button
          class="btn border-0 rounded-0 w-100"
          data-page="bakiyeyukle"
          on:click={() => changePage("bakiyeyukle")}
        >
          <i class="fas fa-money-bill fs-2" />
        </button>
      </div>
    </div>
  </div>
</div>

<style>
  .btn {
    height: 70px;
  }

  .fixed-bottom {
    background-color: #e71f5f;
  }
</style>
