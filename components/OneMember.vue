<script setup lang="ts">
import type { Member } from "@/interface";

interface Props {
  id: number;
}
const props = defineProps<Props>();
const memberList = useState<Map<number, Member>>("memberList");
const member = memberList.value.get(props.id) as Member;

const localNote = computed(() => {
  return member.note || "--";
});

const pointUp = () => {
  member.points++;
};
</script>

<template>
  <section class="box">
    <h4>{{ member.name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>{{ member.id }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ member.email }}</dd>
      <dt>備考</dt>
      <dd>{{ member.note }}</dd>
    </dl>
    <button @click="pointUp">ポイント加算</button>
  </section>
</template>
