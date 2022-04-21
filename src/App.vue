<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      origin: "",
      current: "",
      result: "",
    };
  },

  methods: {
    calculate: function () {
      const origin = +this.origin;
      const current = +this.current;

      if (isNaN(origin) || origin === 0) {
        return;
      }

      if (isNaN(current) || current === 0) {
        return;
      }

      const diff = origin - current;
      this.result = ((diff / origin) * 100).toFixed(2).toString();
    },
    reset() {
      this.origin = "";
      this.current = "";
      this.result = "";
    },
  },
});
</script>

<template>
  <div class="py-8">
    <div class="max-w-xl mx-auto py-12 divide-y md:max-w-4x">
      <h1 class="text-4xl font-bold">體重計算</h1>
      <div class="antialiased text-gray-900 px-6 py-2">
        <div class="">
          <span class="text-gray-700">原體重:</span>
          <input type="text" class="form-input" v-model="origin" />
        </div>
        <div class="">
          <span class="text-gray-700">目前體重：</span>
          <input type="text" class="form-input" v-model="current" />
        </div>
        <div class="py-2">
          <button class="btn btn-blue mr-2" @click="calculate">計算</button>
          <button class="btn btn-blue" @click="reset">重設</button>
        </div>
        <p v-if="result" class="text-gray-700">
          <span class="text-bold">減重率：</span>
          <span class="underline decoration-pink-500">{{ result }} %</span>
        </p>
      </div>
    </div>
  </div>
</template>

<style>
.btn {
  @apply font-bold py-2 px-4 rounded;
}

.btn-blue {
  @apply bg-blue-500 text-white;
}

.btn-blue:hover {
  @apply bg-blue-700;
}

.form-input {
  @apply mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50;
}
</style>
