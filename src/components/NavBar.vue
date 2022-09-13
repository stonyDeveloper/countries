<template>
  <div class="navbar">
    <h2>Where in the world?</h2>
  </div>
</template>

<script>
export default {
  name: "NavBar",
};
</script>

<style scoped>
.navbar {
  height: 70px;
  display: flex;
  font-family: "Nunito Sans", sans-serif;
  color: #000;
  font-size: 15px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 0px 4px 0px;
  display: flex;
  align-items: center;
  background-color: #fff;
  position: sticky;
  top: 0;
  z-index: 90;
  padding-left: 50px;
}
</style>
