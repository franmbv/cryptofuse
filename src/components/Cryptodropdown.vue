<script setup>
import { ref, computed, onMounted, onBeforeUnmount, defineProps } from "vue";

defineProps({
  options: Array,
});

const dropDown = ref(null);
const dropDown2 = ref(null);
let selectedOption = ref(null);
let selectedOption2 = ref(null);

const isDropdownVisible = ref(false);
const isDropdownVisible2 = ref(false);

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
  <div class="dropdown-wrapper" ref="dropDown">
    <div class="dropdown-selected-option" @click="isDropdownVisible = true">
      <img
        v-if="mappedSelectLogo"
        :src="mappedSelectLogo"
        alt="logo"
        width="20"
        height="20"
      />
      {{ mappedSelectOption || "Please select some" }}
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

<div class="icon col" @click="switchValue()">
        <i class="fas fa-exchange-alt"></i>
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
      {{ mappedSelectOption2 || "Please select some" }}
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

</template>

<style scoped>
/* .dropdown-wrapper {
  padding: 16px;
  cursor: pointer;
  max-width: 200px;
  margin: 0 auto;
}

.dropdown-selected-option {
  padding: 16px;
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
}

.option:last-of-type {
  border-bottom-left-radius: 8px;
  border-bottom-right-radius: 8px;
} */

.options-wrapper {
  height: 180px;
  overflow-y: scroll;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
