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
