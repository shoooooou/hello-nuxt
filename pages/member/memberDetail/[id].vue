<script setup lang="ts">
import type { Member } from "@/interface";

const route = useRoute();
const memberList = useState<Map<number, Member>>("memberList");
const member = computed((): Member => {
  const id = Number(route.params.id);
  return memberList.value.get(id) as Member;
});
const localNote = computed((): string => {
  return member.value.note || "--";
});
</script>

<template>
  <h1>会員管理</h1>
  <nav id="breadcrumbs">
    <ul>
      <li><nuxt-link :to="{ name: `index` }">TOP</nuxt-link></li>
      <li>
        <nuxt-link :to="{ name: `member-memberList` }">会員リスト</nuxt-link>
      </li>
      <li>会員詳細情報</li>
    </ul>
  </nav>
  <section>
    <h2>会員詳細情報</h2>
    <dl>
      <dt>ID</dt>
      <dd>{{ member.id }}</dd>
      <dt>名前</dt>
      <dd>{{ member.name }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ member.email }}</dd>
      <dt>保有ポイント</dt>
      <dd>{{ member.points }}</dd>
      <dt>備考</dt>
      <dd>{{ member.note }}</dd>
    </dl>
  </section>
</template>
