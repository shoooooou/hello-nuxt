<script setup lang="ts">
import type { Member } from "@/interface";
const router = useRouter();
const memberList = useState<Map<number, Member>>("memberList");
const member = reactive({
  id: 0,
  name: "",
  email: "",
  points: 0,
  note: "",
});
const onAdd = () => {
  memberList.value.set(member.id, member);
  router.push({ name: "member-memberList" });
};

</script>

<template>
  <section>
    <h2>会員情報追加</h2>
    <p>情報を入力し、登録ボタンをクリックしてください。</p>
    <form @submit.prevent="onAdd">
      <dl>
        <dt><label for="addId">ID&nbsp;</label></dt>
        <dd>
          <input type="number" id="addId" v-model.number="member.id" required />
        </dd>
        <dt><label for="addId">名前&nbsp;</label></dt>
        <dd>
          <input
            type="text"
            id="addName"
            v-model.number="member.name"
            required
          />
        </dd>
        <dt><label for="addId">メールアドレス&nbsp;</label></dt>
        <dd>
          <input
            type="text"
            id="addEmail"
            v-model.number="member.email"
            required
          />
        </dd>
        <dt><label for="addId">保有ポイント&nbsp;</label></dt>
        <dd>
          <input
            type="number"
            id="addPoint"
            v-model.number="member.points"
            required
          />
        </dd>
        <dt><label for="addId">備考&nbsp;</label></dt>
        <dd><textarea id="addNote" v-model="member.note"></textarea></dd>
      </dl>
      <button type="submit">登録</button>
    </form>
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
