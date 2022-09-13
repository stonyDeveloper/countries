<template>
  <div class="search">
    <input type="text" placeholder="Search for a country....." />
  </div>
</template>

<script>
export default {
  name: "SearchInput",
};
</script>

<style scoped>
.search {
  text-align: left;
  padding-left: 50px;
  margin-top: 70px;
  margin-bottom: 30px;
}

input {
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  border: none;
  width: 500px;
  height: 50px;
  padding-left: 25px;
  font-family: "Nunito Sans", sans-serif;
}

input:focus {
  outline: none;
  border: none;
}
</style>
