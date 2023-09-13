<template>
  <div>
    <span v-for="number in numbers">
      <span>{{ number }}, </span>
    </span>
  </div>

  <table class="w-full mt-6 border border-gray-600 bg-white shadow-lg">
    <thead class="w-full bg-gray-500 text-white">
      <tr>
        <td colspan="3" class="px-4 py-2 text-3xl">{{ head }}</td>
      </tr>
    </thead>
    <tr
      class="flex border-b border-gray-400"
      v-for="(item, index) in list"
      key="index"
    >
      <td class="w-2/5 text-2xl px-4 py-2">{{ item.text }}</td>
      <td class="w-1/5 text-2xl px-4 py-2">{{ item.price }}</td>
      <td class="text-2xl px-4 py-2">{{ item.need }}</td>
    </tr>
  </table>

  <form class="mt-4 p-2 bg-white" @click="submitItem">
    <label for="text">
      <input
        model="text"
        placeholder="edit text"
        class="w-2/5 p-2 text-base border"
      />
    </label>
    <label for="price">
      <input
        model="price"
        placeholder="edit price"
        class="w-1/5 p-2 text-base border"
      />
    </label>
    <label for="need">
      <input
        model="need"
        placeholder="edit need"
        class="w-1/5 p-2 text-base border"
      />
    </label>
    <button class="w-1/5 bg-green-500 p-2 text-white">✓</button>
  </form>

  <pre>{{ list[0].text + ' ' + list[0].price + ' ' + list[0].need }}</pre>
</template>

<script setup>
import { ref, reactive, watchEffect } from 'vue';

const head = ref('Shopping List');

let numbers = reactive([1, 2, 4, 8, 16]);
numbers.push(32);
numbers.unshift(0);
let lastNumber = numbers.pop();
let text = ref('');
let price = ref('');
let need = ref(false);

const list = reactive([
  { text: 'milk', price: 4, need: true },
  { text: 'eggs', price: 10, need: true },
  { text: 'butter', price: 5, need: false },
  { text: 'bread', price: 3, need: true },
  { text: 'bacon', price: 7, need: true },
  { text: 'sausage', price: 1, need: false },
  { text: 'juice', price: 12, need: true },
  { text: 'ham', price: 6, need: true },
]);

const submitItem = (text, price, need) => {
  if (text) {
    list.text.push(text);
  }
  if (price) {
    list.price.push(price);
  }
  if (need) {
    list.need.push(need);
  }

  // console.log(text.value, price.value, need.value)
  // list += text.value, price.value, need.value
  // return text.value + price.value + need.value
  list.push.text;
  list.push.price;
  list.push.need;
};

// list[text].value.push("5555")
// list[price].value.push("5555")
// list[need].value.push("5555")

watchEffect(() => {
  console.log(numbers);
  console.log(lastNumber);
});
</script>

<style>
body {
  background: whitesmoke;
  padding: 2rem;
}
</style>
