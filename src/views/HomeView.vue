<template>
  <div class="home">
    <AllCountries />
  </div>
</template>

<script>
// @ is an alias to /src

import AllCountries from "@/components/AllCountries.vue";

export default {
  name: "HomeView",
  components: {
    AllCountries,
  },
};
</script>
