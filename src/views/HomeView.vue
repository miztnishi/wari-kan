<template class="main">
  <warikan />
</template>

<script lang="ts">
import { defineComponent } from "vue";

// Components
import Warikan from "../components/warikan.vue";

export default defineComponent({
  name: "HomeView",

  components: {
    Warikan,
  },
});
</script>

<style scoped>
.main {
  text-align: center;
}
</style>
