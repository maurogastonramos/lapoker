<template>
  <div class="h-full">
    <!-- Login -->
    <div v-if="!userIsLogged">
      <Login @init="loginHandler"></Login>
    </div>

    <!-- Board -->
    <div v-else class="h-full p-4 flex flex-col">
      <Board :player-name="playerName" :session-id="sessionId"></Board>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

import Login from "./pages/Login.vue";
import Board from "./pages/Board.vue";

let userIsLogged = ref(false);
let playerName = ref("");
let sessionId = ref("");

function loginHandler(value){
  playerName.value = value.name;
  sessionId.value = value.sessionId;
  userIsLogged.value = true;
}
</script>
