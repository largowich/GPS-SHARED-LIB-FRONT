<script setup lang="ts">
import BasicButton from "./BasicButton.vue";
import "../css/header.css";

interface Props {
  user: Record<string, unknown>;
}

interface Emit {
  (e: "login"): void;
  (e: "logout"): void;
  (e: "createAccount"): void;
}

const props = defineProps<Props>();

const emit = defineEmits<Emit>();
</script>

<template>
  <header>
    <div class="wrapper">
      <div>
        <img
          alt="Vue logo"
          class="logo"
          src="./assets/logo.svg"
          width="64"
          height="32"
        />
        <h1>GPS</h1>
      </div>
      <div>
        <basic-button
          size="small"
          @click="emit('logout')"
          label="Log out"
          v-if="props.user"
        />
        <basic-button
          size="small"
          @click="emit('login')"
          label="Log in"
          v-if="!props.user"
        />
        <basic-button
          primary
          size="small"
          @click="emit('createAccount')"
          label="Sign up"
          v-if="!props.user"
        />
      </div>
    </div>
  </header>
</template>
