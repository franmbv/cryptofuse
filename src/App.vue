<script setup>
import NavBar from "./components/NavBar.vue";
import SwapForm from "./components/SwapForm.vue";
import Footer from "./components/Footer.vue";
import Carousel from "./components/Carousel.vue";
import CryptoFile from "./assets/crypto_file.json";

</script>

<template>
  <NavBar />

  <section class="text-center body colored-section">
    <div class="row align-items-center">
      <div class="col align-middle title">
        <img
          src="./assets/logo_crytofuse.png"
          alt="cryptofuse-logo"
          class="title_logo"
        />
      </div>
      <SwapForm 
          :options = "options"
      />
    </div>
  </section>

  <section class="white-section text-center" id="aboutUs">
    <div class="row">
      <h1 class="col align-self-center">About us</h1>
      <div class="container px-4 py-4" id="featured-3">
        <div class="row g-4 py-5 row-cols-1 row-cols-lg-3">
          <div class="feature col">
            <div
              class="feature-icon d-inline-flex align-items-center justify-content-center bg-gradient fs-2 mb-3"
            >
              <i class="fas fa-user-clock"></i>
            </div>
            <h3 class="fs-2">Faster</h3>
            <p>
              We are one of the companies whose process is one of the fastest.
              All our users highlight the immediacy.
            </p>
          </div>
          <div class="feature col">
            <div
              class="feature-icon d-inline-flex align-items-center justify-content-center  bg-gradient fs-2 mb-3"
            >
              <i class="fas fa-user-shield"></i>
            </div>
            <h3 class="fs-2">Trust</h3>
            <p>
              Before, during and after we guarantee absolute communication if
              you have any questions.
            </p>
          </div>
          <div class="feature col">
            <div
              class="feature-icon d-inline-flex align-items-center justify-content-center bg-gradient fs-2 mb-3"
            >
              <i class="fas fa-users"></i>
            </div>
            <h3 class="fs-2">User favorite</h3>
            <p>
              We have completed more than 5 thousand operations, our clients
              come from more than 80 countries
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="text-center colored-section" id="topPairs">
    <div class="row align-items-center">
      <div class="col-12 col-lg-6 " >
        <h1>Top Swapped Pairs</h1>
      </div>
      <Carousel />
    </div>
  </section>

  <Footer />
</template>

<style scoped>
.body {
  padding: 90px;
  overflow-x: hidden
}
.title {
  width: 100%;
}

.title_logo {
  width: 60%;
}

h1 {
  font-family: "Roboto", sans-serif;
  font-size: 5rem;
  color: #ffffff;
}

#aboutUs {
  padding: 50px 20px;
}
.white-section h1 {
  padding-top: 10px;
  font-size: 4rem;
  color: #03c988;
}

.white-section h3 {
  color: #03c988;
}

i:hover{
  color: #03c988;
}

@media (max-width: 700px) {
 .title_logo{
    width: 80%;
    padding-bottom: 30px
    
 }

}

</style>
