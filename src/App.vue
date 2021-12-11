<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <div>
    <span>count: {{ count }}</span
    ><br />
    <span>count1: {{ count1 }}</span
    ><br />
    <button @click="onPlus">plus</button>
    <button @click="onPlus1">plus1</button>
  </div>
  <router-view />
</template>
<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    let count = 0; // No side effect ตัวแปรเปลี่ยนค่าแต่ไม่ส่งผลในหน้า UI
    const count1 = ref<number>(0); // side effect ตัวแปรเปลี่ยนค่าและส่งผลในหน้า UI
    const onPlus = () => {
      count = count + 1;
      console.log(count);
    };

    const onPlus1 = () => {
      count1.value = count1.value + 1;
      console.log(count1);
    };
    return {
      count,
      count1,
      onPlus,
      onPlus1,
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
