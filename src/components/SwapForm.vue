<script setup>
import { ref, computed, onMounted, onBeforeUnmount, defineProps } from "vue";
import CryptoFile from "../assets/crypto_file.json";
import CryptoDropdown from "../components/Cryptodropdown.vue";

defineProps({
  options: Array,
});

const rate = ref("");
const amountOne = ref(1);
const amountTwo = ref(0);
const options = ref(CryptoFile);
const dropDown = ref(null);
const dropDown2 = ref(null);
let selectedOption = ref(null);
let selectedOption2 = ref(null);
const isDropdownVisible = ref(false);
const isDropdownVisible2 = ref(false);

// const fetchData = () =>{
//    fetch(`${selectedOption}`)
//   .then(res => res.json())
//   .then(data => {
//      currencyData.value = data
//      rate.value = data.conversion_rates[selectedOption2]
//      amountTwo.value = amountOne.value * rate.value
// })
// }

// onMounted(() => {
//     fetchData()
// })

const toggleOptionSelect = (option) => {
  selectedOption.value = option;
};

const toggleOptionSelect2 = (option) => {
  selectedOption2.value = option;
};

const mappedSelectOption = computed({
  get() {
    return selectedOption.value?.crypto_info.name || selectedOption.value;
  },
});

const mappedSelectOption2 = computed({
  get() {
    return selectedOption2.value?.crypto_info.name || selectedOption2.value;
  },
});

const mappedSelectLogo = computed({
  get() {
    return selectedOption.value?.crypto_info.image || selectedOption.value;
  },
});

const mappedSelectLogo2 = computed({
  get() {
    return selectedOption2.value?.crypto_info.image || selectedOption2.value;
  },
});

const closeDropdown = (element) => {
  if (!dropDown.value.contains(element.target)) {
    isDropdownVisible.value = false;
  }
};

const closeDropdown2 = (element) => {
  if (!dropDown2.value.contains(element.target)) {
    isDropdownVisible2.value = false;
  }
};

const switchValue = () => {
  let temporaryValue = selectedOption.value;
  selectedOption.value = selectedOption2.value;
  selectedOption2.value = temporaryValue;
};

onMounted(() => {
  window.addEventListener("click", closeDropdown);
  window.addEventListener("click", closeDropdown2);
});

onBeforeUnmount(() => {
  window.removeEventListener("click", closeDropdown);
  window.removeEventListener("click", closeDropdown2);
});
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

    <div class="dropdown-wrapper" ref="dropDown">
      <div class="dropdown-selected-option" @click="isDropdownVisible = true">
        <img
          v-if="mappedSelectLogo"
          :src="mappedSelectLogo"
          alt="logo"
          width="20"
          height="20"
        />
        {{ mappedSelectOption || "Select one" }}
      </div>

      <Transition name="fade">
        <div class="options-wrapper" v-if="isDropdownVisible">
          <div
            class="option"
            v-for="(option, index) in options"
            :key="index"
            @click="toggleOptionSelect(option)"
          >
            <img
              :src="option.crypto_info.image"
              alt="logo"
              width="20"
              height="20"
            />
            {{ option.crypto_info.name }}
          </div>
        </div>
      </Transition>
    </div>

    <div class="icon col">
      <i class="fas fa-exchange-alt" @click="switchValue()"></i>
    </div>

    <div class="dropdown-wrapper" ref="dropDown2">
      <div class="dropdown-selected-option" @click="isDropdownVisible2 = true">
        <img
          v-if="mappedSelectLogo2"
          :src="mappedSelectLogo2"
          alt="logo"
          width="20"
          height="20"
        />
        {{ mappedSelectOption2 || "Select two" }}
      </div>

      <Transition name="fade">
        <div class="options-wrapper" v-if="isDropdownVisible2">
          <div
            class="option"
            v-for="(option, index) in options"
            :key="index"
            @click="toggleOptionSelect2(option)"
          >
            <img
              :src="option.crypto_info.image"
              alt="logo"
              width="20"
              height="20"
            />
            {{ option.crypto_info.name }}
          </div>
        </div>
      </Transition>
    </div>

    <div class="exchange-rate form-text">
      {{ amountOne }} {{ mappedSelectOption || "Crypto" }} = {{ amountTwo }}
      {{ mappedSelectOption2 }}
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

/* Nuevo css */

.dropdown-wrapper {
  padding: 10px;
  cursor: pointer;
  max-width: 200px;
  margin: 0 auto;
}

.dropdown-selected-option {
  padding: 10px;
  border: solid 1px #313131;
  border-radius: 8px;
  box-sizing: border-box;
  margin-bottom: 4px;
}

.option:hover {
  background: #c5c5c5;
}

.option {
  padding: 16px;
  border: solid 1px #313131;
  box-sizing: border-box;
  background-color: white;
}

.option:last-of-type {
  border-bottom-left-radius: 8px;
  border-bottom-right-radius: 8px;
}

.options-wrapper {
  width: 180px;
  height: 180px;
  overflow-y: scroll;
  position: absolute;
  z-index: 99999;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Hasta aqui */
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
 .options-wrapper {
  width: 43%;
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
