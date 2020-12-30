<template>
  <div class="password">
    <h1>Password is: {{ password }}</h1>
    <br />
    <button class="angled-gradient-button" v-on:click="generatePassword">
      <img src="../assets/arrows-counter-clockwise-duotone.svg" />Regenerate
      Password
    </button>
    <button class="angled-gradient-button" v-on:click="copyToClipboard">
      <img src="../assets/copy-duotone.svg" />Copy Password
    </button>
    <ul>
      <li>
        <label for="passLength">{{ length }}</label> <br />
        Length
        <input
          type="range"
          min="1"
          max="128"
          id="passLength"
          name="passLength"
          v-model="length"
        />
      </li>
      <li>
        <label for="capital">{{ capital }}</label> <br />
        A-Z
        <input
          type="checkbox"
          id="capital"
          name="capital"
          value="capital"
          v-model="capital"
        />
      </li>
      <li>
        <label for="lowercase">{{ lowercase }}</label> <br />
        a-z
        <input
          type="checkbox"
          id="lowercase"
          name="lowercase"
          value="lowercase"
          v-model="lowercase"
        />
      </li>
      <li>
        <label for="number">{{ number }}</label> <br />
        0-9
        <input
          type="checkbox"
          id="number"
          name="number"
          value="number"
          v-model="number"
        />
      </li>
      <li>
        <label for="special">{{ special }}</label> <br />
        !@#$%^*
        <input
          type="checkbox"
          id="special"
          name="special"
          value="special"
          v-model="special"
        />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Password",
  data() {
    return {
      password: "",
      length: 14,
      capital: false,
      lowercase: true,
      number: false,
      special: true,
    };
  },
  methods: {
    generatePassword() {
      let finalResult = "";
      const capitalChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
      const lowercaseChars = "abcdefghijklmnopqrstuvwxyz"
      const numbers = "0123456789"
      const specialChars = "!@#$%^&*"
      let allCharacters = []

      if (this.capital == true){
        allCharacters.push(capitalChars)
      }
      if (this.lowercase == true){
        allCharacters.push(lowercaseChars)
      }
      if (this.number == true){
        allCharacters.push(numbers)
      }
      if (this.special == true){
        allCharacters.push(specialChars)
      }

      allCharacters = allCharacters.join("")
      let charactersLength = allCharacters.length

      for (var i = 0; i < this.length; i++) {
        finalResult += allCharacters.charAt(
          Math.floor(Math.random() * charactersLength)
        );
      }
      return this.password = finalResult;
    },
    async copyToClipboard() {
      if (!navigator.clipboard) return;
      await navigator.clipboard.writeText(this.password);
    },
  },
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
  box-shadow: 0 0.2em 0.3em rgba(0, 0, 0, 0.15);
  color: #3721a7;
  background-color: transparent;
  background-position: 100%;
  border: 3px solid #3721a7;
  text-transform: uppercase;
  padding: 8px 16px;
  border-radius: 3px;
  transition: all 0.2s ease-out;
  font-weight: 900;
  cursor: pointer;
  letter-spacing: 2px;
  background-image: linear-gradient(
    110deg,
    #3721a7 0%,
    #3721a7 50%,
    transparent 50%,
    transparent 100%
  );
  font-size: 14px;
}
.angled-gradient-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 0 0.3em rgba(0, 0, 0, 0.25);
  background-position: 0;
  color: #fff;
}
.angled-gradient-button:active {
  transform: translateY(-1px);
}
</style>
