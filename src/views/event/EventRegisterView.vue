<script setup lang="ts">
import { type EventItem } from "@/type";

import type { PropType } from "vue";

import { useRouter } from "vue-router";
import { useMessageStore } from "@/stores/message";

const props = defineProps({
  event: {
    type: Object as PropType<EventItem>,
    required: true,
  },
});
const router = useRouter();
const store = useMessageStore();

function register() {
  store.updateMessage("Registration successful for " + props.event?.title);
  setTimeout(() => {
    store.resetMessage();
  }, 3000);
  router.push({
    name: "event-detail",
    params: {
      id: props.event?.id,
    },
  });
}
</script>
<template>
  <p>Registration from here</p>
  <button class="button-13" @click="register">Register Me</button>
</template>

<style>
.button-13 {
  background-color: #fff;
  border: 1px solid #d5d9d9;
  border-radius: 8px;
  box-shadow: rgba(213, 217, 217, .5) 0 2px 5px 0;
  box-sizing: border-box;
  color: #0f1111;
  cursor: pointer;
  display: inline-block;
  font-family: "Amazon Ember",sans-serif;
  font-size: 13px;
  line-height: 29px;
  padding: 0 10px 0 11px;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
  width: 200px;
}

.button-13:hover {
  background-color: #f7fafa;
}

.button-13:focus {
  border-color: #008296;
  box-shadow: rgba(213, 217, 217, .5) 0 2px 5px 0;
  outline: 0;
}
</style>

