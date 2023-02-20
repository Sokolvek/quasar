<script setup>
import { RouterLink } from "vue-router";
</script>
<template>
  <main>
    <button @click="combatTest()">напасть на монстра</button>

    <button @click="attack">атаковать монстра</button>

    <!-- <div class="battle-logs" ref="combatLogs">
      <p v-for="combatLog in combatLogs">{{ combatLog }}</p>
    </div> -->
  </main>
</template>

<script>
import { defineComponent } from "vue";
import { storeToRefs } from "pinia";
import { usePostStore } from "../stores/post";
import { ref } from "vue";
const { posts, loading, error } = storeToRefs(usePostStore());
const { fetchPosts, fetchPost } = usePostStore();
import { useCounterStore } from "src/stores/store";

import "../assets/styles/main.less";

export default defineComponent({
  name: "IndexPage",
  data() {
    return { text: ref(""), text1: ref(""), text2: ref(""), combatLogs: [] };
  },
  async mounted() {
    await fetchPosts();
    await console.log(posts);
  },
  setup() {
    const store = usePostStore();
    const count = computed(() => store.title);
    const doubleCountValue = computed(() => store.title);

    return {
      store,
      count,
      doubleCountValue,
    };
  },

  methods: {
    combatTest() {
      if(!useCounterStore.combat){
        useCounterStore.combat = true;
        console.log(useCounterStore.combat);
        this.combatLogs.push("Fight Started")

      }else if(useCounterStore.combat){
        this.combatLogs.push("You Already in Fight")
      }
    },
    attack() {
      if (useCounterStore.combat) {
        this.combatLogs.push("Attack")
      }
    },
  },
});
</script>
