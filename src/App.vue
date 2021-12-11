<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <div>
    <span>{{ account1.data }}</span
    ><br />
    <span>{{ count }}</span
    ><br />
    <button @click="onClickClear">Clear</button>
  </div>
  <router-view />
</template>
<script lang="ts">
import { defineComponent, ref, onMounted, reactive } from "vue";

const defaultAcc = { username: "", password: "" };

export default defineComponent({
  setup() {
    const count = ref<number>(0);
    const account = reactive({ username: "admin", password: "123456" }); // input object only
    const account1 = reactive({
      data: { username: "admin", password: "123456" },
    });
    const onClickClear = () => {
      // account.username = "";
      // account.password = "";
      account1.data = defaultAcc;
    };

    const onPlus = () => {
      count.value = count.value + 1;
    };

    onMounted(() => {
      setInterval(onPlus, 1000);
    });

    return {
      account,
      account1,
      onClickClear,
      onMounted,
      count,
    };
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
