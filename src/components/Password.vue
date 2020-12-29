<template>
  <div class="password">
    <h1>{{ password }}</h1>
    <br>
    <button class='angled-gradient-button'> <img src="../assets/arrows-counter-clockwise-duotone.svg"/>Generate Password</button>
    <button class='angled-gradient-button'><img src="../assets/copy-duotone.svg"/>Copy Password</button>
    
  </div>
</template>

<script>
export default {
  name: "Password",
  props: {
    password: String
  }
};
</script>

<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.angled-gradient-button {
    background-size: 220%;
    box-shadow: 0 .2em .3em rgba(0, 0, 0, 0.15);
    color: #3721a7;
    background-color: transparent;
    background-position: 100%;
    border: 3px solid #3721a7;
    text-transform: uppercase;
    padding: 8px 16px;
    border-radius: 3px;
    transition: all .2s ease-out;
    font-weight: 900;
    cursor: pointer;
    letter-spacing: 2px;
    background-image: linear-gradient(110deg, #3721a7 0%, #3721a7 50%, transparent 50%, transparent 100%);
    font-size: 14px;
}
.angled-gradient-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 0 .3em rgba(0, 0, 0, 0.25);
    background-position: 0;
    color: #fff;
}
.angled-gradient-button:active {
    transform: translateY(-1px);
}
</style>
