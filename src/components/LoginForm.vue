<template>
  <div>
    <h1>Login</h1>
    <br />
    <span>{{ user }}</span>
    <form>
      <label for="username">Username</label>
      <input
        type="text"
        name="username"
        id="username"
        v-model="from_data.account.username"
      />
      <br />
      <label for="password">Password</label>
      <input
        type="text"
        name="password"
        id="password"
        v-model="from_data.account.password"
      />
      <br />
      {{ from_data.account }}
      <button type="button">Submit</button>
      <button type="button" @click="onClear">Clear</button>
    </form>
  </div>
</template>
<script lang="ts">
import { defineComponent, reactive } from "vue";

export default defineComponent({
  props: ["user"],
  setup() {
    const from_data = reactive({ account: { username: "", password: "" } });
    const onClear = () => {
      from_data.account = { username: "", password: "" };
    };
    return { from_data, onClear };
  },
});
</script>
