<script setup>
const { data } = await useFetch("/api/tickers?limit=10");
</script>

<template>
  <main class="antialiased  text-slate-700 mx-2">
    <div
      class="
        max-w-lg
        mx-auto
        my-10
        bg-white
        p-8
        rounded-xl
        shadow shadow-slate-300
      "
    >
      <div class="flex flex-col justify-between items-center">
        <div>
          <h2 class="text-3xl font-bold underline">Index Page</h2>
        </div>
        <div class="flex justify-between items-center border-b border-slate-200 py-3 px-2 border-l-4  border-l-transparent">
          <table border="1 px solid">
            <thead>
              <tr class="inline-flex items-center space-x-2">
                <th>Name</th>
                <th>Symbol</th>
                <th>Price</th>
                <th>Details</th>
              </tr>
            </thead>
            <tr v-for="currency in data.data" :key="data.data.id" class="flex justify-between items-center border-b border-slate-200 py-3 px-1 border-l-4  border-l-transparent" >
              <td>{{ currency.name }}</td>
              <td>{{ currency.symbol }}</td>
              <td>{{ currency.price_usd }}</td>
              <td>
                <NuxtLink :to="'/currency/' + currency.id">{{
                  currency.id
                }}</NuxtLink>
              </td>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </main>
</template>
<style scoped>
</style>
