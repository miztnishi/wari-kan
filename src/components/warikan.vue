<template>
  <div class="warikan mt-4">
    <h1>割り勘計算</h1>
    <div class="d-flex flex-row justify-center">
      <div class="d-flex flex-row align-center mx-4">
        <span class="body-1-noto-sans mx-2">人数</span>
        <v-text-field class="component-text-field" v-model="peopleCount" />人
      </div>
      <div class="d-flex flex-row align-center mx-4">
        <span class="body-1-noto-sans mx-2">金額</span>
        <v-text-field class="component-text-field" v-model="amount" />円
      </div>
    </div>
    <div>割り勘人数:{{ peopleCount }}人、合計金額 {{ amountFormat }}円</div>
    <v-divider></v-divider>
    <h3>一人当たり金額</h3>
    <div>{{ amountForEachPerson }}円</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export interface DataType {
  peopleCount: number;
  amount: number;
}
export default defineComponent({
  name: "wari-kan",
  data(): DataType {
    return {
      peopleCount: 0,
      amount: 0,
    };
  },
  computed: {
    amountFormat(): string {
      if (!isNaN(Number(this.amount))) {
        return Number(this.amount).toLocaleString();
      } else {
        return "0";
      }
    },
    amountForEachPerson(): string {
      if (
        isNaN(Number(this.amount)) ||
        isNaN(Number(this.peopleCount)) ||
        this.peopleCount === 0 ||
        this.amount === 0
      ) {
        return "0";
      }
      return (this.amount / this.peopleCount).toLocaleString();
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.warikan {
  margin: auto;
  text-align: center;
}

.v-text-field {
  min-width: 100px;
  text-align: right;
}
</style>
