<template>
    <div class="battle-logs" ref="combatLogs">
      <p v-for="combatLog in combatLogs">{{ combatLog }}</p>
    </div>
</template>

<script>

import { storeToRefs } from "pinia";

export default{
    data(){
        return{
            combatLogs: []

        }
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
}
</script>