<template>
  <div>
    <h1>Login</h1>
    <br />
    <span>{{ user }}</span>
  </div>
</template>
<script lang="ts">
import { defineComponent, onMounted } from "vue";

export default defineComponent({
  props: ["user"],
  setup(props) {
    onMounted(() => {
      console.log(props.user);
    });
    return { onMounted };
  },
});
</script>
