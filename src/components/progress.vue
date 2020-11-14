<template>
  <div class="progress">
    <div
      class="progress-bar bg-primary"
      role="progressbar"
      :style="{ width: progress + '%' }"
      aria-valuenow="50"
      aria-valuemin="0"
      aria-valuemax="100">
      <b>{{ currentItem }}/10</b>
    </div>
  </div>
</template>

<script>
import { EventBus } from "../main";

export default {
  data() {
    return {
      currentItem: 0,
      progress: 0,
    };
  },
  created() {
    EventBus.$on("sendProgressBar", (productListCount) => {
      this.progress = productListCount * 10;
      this.currentItem = productListCount;
    });
  },
};
</script>