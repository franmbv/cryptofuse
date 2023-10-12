<script setup>
import CryptoFile from "../assets/crypto_file.json";

const cryptoImages = CryptoFile;
</script>

<template>
  <div
    id="carouselExampleSlidesOnly"
    class="carousel slide col-12 col-lg-6 row align-items-center"
    data-bs-ride="carousel"
  >
    <div class="carousel-inner col">
      <div class="carousel-item active">
        <h2>Btc to Ban</h2>
        <img
          :src="cryptoImages[4].crypto_info.image"
          alt="BTC logo"
          width="100"
          height="110"
        />
        &nbsp;
        <i class="fas fa-exchange-alt"></i>
        &nbsp;
        <img
          :src="cryptoImages[0].crypto_info.image"
          alt="BAN logo"
          width="100"
          height="110"
        />
      </div>
      <div class="carousel-item">
        <h2>Eth to Btc</h2>
        <img
          :src="cryptoImages[5].crypto_info.image"
          alt="ETH logo"
          width="100"
          height="110"
        />
        &nbsp;
        <i class="fas fa-exchange-alt"></i>
        &nbsp;
        <img
          :src="cryptoImages[4].crypto_info.image"
          alt="BTC logo"
          width="100"
          height="110"
        />
      </div>
      <div class="carousel-item">
        <h2>Sol to Eth</h2>
        <img
          :src="cryptoImages[3].crypto_info.image"
          alt="SOL logo"
          width="100"
          height="110"
        />
        &nbsp;
        <i class="fas fa-exchange-alt"></i>
        &nbsp;
        <img
          :src="cryptoImages[5].crypto_info.image"
          alt="ETH logo"
          width="100"
          height="110"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
h2 {
  font-size: 3rem;
  color: #03c988;
}

.carousel {
  padding: 200px 0;
  font-family: "Poppins", sans-serif;
  font-size: 2.5rem;
  background-color: #ffffff;
  border-radius: 15px;
  background-image: url("https://www.transparenttextures.com/patterns/batthern.png");
}

.fa-exchange-alt {
  color: #03c988;
}
</style>
