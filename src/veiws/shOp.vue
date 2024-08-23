<template>
  <div>
    <div>
      <h2>Visitor Count: {{ visitorCount }}</h2>
      <button @click="incrementCount">Increment Count</button>
    </div>

    <!-- Your existing code continues here -->
    <p class="px-20 mt-4">
      <!-- Font Awesome icons and other content -->
    </p>
    <!-- Remaining code -->
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Card from '../components/carD.vue';
import store from '../store/index';

let carditem = ref([]);
let catogress = ref([]);
let selected = ref(['all']);
let visitorCount = ref(0);

let getProduct = () => {
  store.dispatch('product/get').then((res) => {
    carditem.value = res;
  });
};

let fetchVisitorCount = () => {
  fetch('https://shop-le2d.onrender.com/visitorCount')
    .then(response => response.json())
    .then(data => {
      visitorCount.value = data.count;
    });
};

let getCatogress = () => {
  store.dispatch('catogress/get').then((res) => {
    catogress.value = res.Catogress;
  });
};

let filterPro = () => {
  if (selected.value[0] === 'all') {
    getProduct();
  } else {
    store.dispatch('catogress/filter', selected.value[0]).then(res => {
      carditem.value = res;
    });
  }
};

let incrementCount = () => {
  visitorCount.value++;
};

onMounted(() => {
  getProduct();
  getCatogress();
  fetchVisitorCount();
});

let card = ref(true);
let hidecat = ref(false);
</script>

<style scoped>
/* Your existing styles */
</style>
