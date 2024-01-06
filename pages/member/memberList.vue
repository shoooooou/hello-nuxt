<script setup lang="ts">
import type { Member } from "../../interface";

const memberList = useState<Map<number, Member>>("memberList");
</script>

<template>
  <h1>会員管理</h1>
  <nav id="breadcrumbs">
    <ul>
      <li><NuxtLink :to="{ name: `index` }">TOP</NuxtLink></li>
      <li>会員リスト</li>
    </ul>
  </nav>
  <section>
    <h2>会員リスト</h2>
    <p>
      新規登録は<NuxtLink :to="{ name: `member-memberList-memberAdd` }"
        >こちら</NuxtLink
      >
    </p>
    <ul>
      <li v-for="[id, member] in memberList" :key="id">
        <NuxtLink
          :to="{
            name: `member-memberList-memberDetail-id`,
            params: { id: id },
          }"
        >
          IDが{{ id }}の{{ member.name }}さん
        </NuxtLink>
      </li>
    </ul>
  </section>
  <NuxtPage />
</template>
<style scoped>
#breadcrumbs ul li {
  display: inline;
  list-style-type: none;
}
#breadcrumbs {
  margin-left: 10px;
}
#breadcrumbs ul {
  padding-left: 10px;
}
#breadcrumbs ul li:before {
  content: ">";
  padding-right: 10px;
}
#breadcrumbs ul li:first-child:before {
  content: none;
}
</style>
```
