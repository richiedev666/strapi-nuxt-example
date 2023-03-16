<script setup lang="ts">
import type { Landing } from "~/types";

const { find } = useStrapi();

const { data, pending, refresh, error } = await useAsyncData(
  "landing",
  async () => {
    const response = await find<Landing>("landing");

    return response?.data?.attributes;
  }
);
</script>

<template>
  <div>
    <h1>{{ data.title }}</h1>
  </div>
</template>
