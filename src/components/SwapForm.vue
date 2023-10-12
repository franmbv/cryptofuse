<script setup>
import { ref, onMounted } from "vue";
import CryptoFile from "../assets/crypto_file.json";

const crypto = ref(CryptoFile);

const currencyData = ref([]);
const currency_one = ref("BTC");
const currency_two = ref("BAN");
const rate = ref("");
const amountOne = ref(1);
const amountTwo = ref(0);

// const fetchData = () =>{
//    fetch(`${currency_one}`)
//   .then(res => res.json())
//   .then(data => {
//      currencyData.value = data
//      rate.value = data.conversion_rates[currency_two]
//      amountTwo.value = amountOne.value * rate.value
// })
// }

const switchValues = () => {
  const temporaryValue = currency_one.value;
  currency_one.value = currency_two.value;
  currency_two.value = temporaryValue;
};

// onMounted(() => {
//     fetchData()
// })
</script>

<template>
  <form action="#" class="col-12 col-lg-6">
    <div class="amount">
      <label for="input-one" class="form-text">Enter amount</label>
      <input
        class="form-control"
        type="number"
        name="input-one"
        id="input-one"
        v-model="amountOne"
      />
    </div>
    <div class="drop-list row row align-items-center">
      <div class="from col">
        <div class="select-box">
          <label for="first-currency" class="form-text">From</label>

          <select
            name="first-currency"
            id="first-currency"
            v-model="currency_one"
            class="form-select"
          >
            <option
              v-for="currency in crypto"
              :value="currency.crypto_key"
              :key="currency.crypto_key"
            >
              {{ currency.crypto_key }}
            </option>
          </select>
        </div>
      </div>
      <div class="icon col" @click="switchValues()">
        <i class="fas fa-exchange-alt"></i>
      </div>
      <div class="to col">
        <div class="select-box">
          <label to="second-currency" class="form-text">To</label>

          <select
            name="second-currency"
            id="second-currency"
            v-model="currency_two"
            class="form-select"
          >
            <!-- Options tag are inserted from JavaScript -->
            <option
              v-for="currency in crypto"
              :value="currency.crypto_key"
              :key="currency.crypto_key"
            >
              {{ currency.crypto_key }}
            </option>
          </select>
        </div>
      </div>
    </div>
    <div class="exchange-rate form-text">
      {{ amountOne }} {{ currency_one }} = {{ amountTwo }} {{ currency_two }}
      &nbsp
      <i class="fas fa-info-circle fa-xs">
        <span class="tooltiptext">Demo rate</span></i
      >
    </div>
    <button class="btn btn-outline-success">Exchange</button>
  </form>
</template>

<style scoped>
form {
  background-color: white;
  border-radius: 10px;
  color: #03c988;
}

.form-text {
  display: block;
  font-size: 18px;
  margin-bottom: 5px;
  color: gray;
}

.amount {
  margin: 15px;
}

input:hover,
select:hover {
  background-color: #f2f2f2;
}
.drop-list {
  margin: 15px;
}

.fa-info-circle .tooltiptext {
  visibility: hidden;
  width: 200px;
  height: 20px;
  color: #ffffff;
  text-align: center;
  border-radius: 6px;
  padding: 5px 0;
  background-color: #000000;
  /* Position the tooltip */
  position: absolute;
  z-index: 1;
}

.fa-info-circle:hover .tooltiptext {
  visibility: visible;
}
.btn {
  margin: 15px;
}

@media (max-width: 700px) {
  .drop-list .select-box {
    width: 115px;
    height: 45px;
  }

  .fa-exchange-alt {
    padding-top: 40px;
    padding-right: 28px;
  }

  .exchange-rate {
    padding-top: 20px;
  }
  .fa-info-circle .tooltiptext {
    width: 50px;
    height: 40px;
    padding: 5px 0;
  }
}
</style>
