<script setup lang="ts">
import type { Member } from "@/interface";

useState<Map<number, Member>>("memberList", () => {
  const memberListInit = new Map<number, Member>();
  memberListInit.set(33456, {
    id: 33456,
    name: "サンプル１",
    email: "sample1@yahoo.co.jp",
    points: 100,
    note: "初回入会特典あり",
  });
  memberListInit.set(33457, {
    id: 33457,
    name: "サンプル2",
    email: "sample2@yahoo.co.jp",
    points: 200,
    note: "初回入会特典なし",
  });
  return memberListInit;
});
</script>
<template>
  <header>
    <h1>ルーティングサンプル</h1>
  </header>
  <main>
    <NuxtPage />
  </main>
</template>
