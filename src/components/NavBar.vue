<script setup>
defineProps(["title"]);
</script>

<template>
  <nav class="navbar navbar-expand-lg colored-section">
    <section class="container-fluid">
      <a class="navbar-brand" href="#">
        <img
          src="/src/assets/logo_crytofuse.png"
          alt="Logo"
          width="40"
          height="34"
          class="d-inline-block align-text-top"
        />
        <p>CryptoFuse</p>
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link" href="#aboutUs"> About Us </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#topPairs"> Top Pairs </a>
          </li>
           <li class="nav-item">
            <a class="nav-link" href="#"> Discord </a>
          </li>
           <li class="nav-item">
            <a class="nav-link" href="#contact"> Contact Us </a>
          </li>
        </ul>
      </div>
    </section>
  </nav>
</template>

<style scoped>
.navbar-brand {
  padding: 30px 50px 30px 75px;
}

.nav-item {
  padding-left: 20px;
}

.nav-item:hover {
  background-color: #03c988;
}

p{
  padding-left: 5px;
  display: inline;
}

@media (max-width: 700px) {

p{
  display:none
}

}

</style>
