<script setup lang="ts">
// レスポンスの型注釈
type Geo = {
  lat: string;
  lng: string;
};

type Address = {
  street: string;
  suite: string;
  city: string;
  zipcode: string;
  geo: Geo;
};

type Company = {
  name: string;
  catchPhrase: string;
  bs: string;
};

type User = {
  id: number;
  name: string;
  username: string;
  email: string;
  address: Address;
  phone: string;
  website: string;
  company: Company;
};

const { data: users, error, pending } = await useFetch<User[]>("https://jsonplaceholder.typicode.com/users");
useHead({
  title: "Nuxt App", // titleタグ設定
  link: [
    // GoogleFonts設定
    {
      rel: "stylesheet",
      href: "https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;700&display=swap",
    },
  ],
});
</script>
<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
      <p v-if="pending">データ読み込み中...</p>
      <p v-else-if="error">エラーが発生しました: {{ error?.message }}</p>
      <ul>
        <li v-for="user in users" :key="user.id">{{ user.id }} : {{ user.name }}</li>
      </ul>
      <!-- <img src="~/assets/cat.jpg" alt="" />
      <img src="/cat.jpg" alt="" /> -->
    </NuxtLayout>
  </div>
</template>
