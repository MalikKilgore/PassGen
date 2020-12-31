<template>
  <div
    style="
      display: flex;
      flex-direction: column;
      border: black solid 5px;
      max-width: 55%;
    "
  >
    <!-- Cover -->
    <div style="max-height: fit-content; width: 100%; border-bottom: 2px solid black">
      <h1>Password is: {{ password }}</h1>
      <br />
      <button class="angled-gradient-button" v-on:click="generatePassword">
        <img src="../assets/arrows-counter-clockwise-duotone.svg" /> <br>
        Regenerate Password
      </button>
      <button class="angled-gradient-button" v-on:click="copyToClipboard">
        <img src="../assets/copy-duotone.svg" /> <br>
        Copy Password
      </button>
    </div>
    <br />
    <!-- Content -->
    <div style="/* Take available height */ flex: 1">
      <ul>
        <li >
          <label for="passLength">Length: {{ length }}</label>
          <input
            type="range"
            min="1"
            max="128"
            id="passLength"
            name="passLength"
            v-model="length"
          />
        </li>
        <br />
        <li>
          <label for="capital">A-Z</label>
          <input
            type="checkbox"
            id="capital"
            name="capital"
            value="capital"
            v-model="capital"
          />
        </li>
        <br />
        <li>
          <label for="lowercase">a-z</label>
          <input
            type="checkbox"
            id="lowercase"
            name="lowercase"
            value="lowercase"
            v-model="lowercase"
          />
        </li>
        <br />
        <li>
          <label for="number">0-9</label>
          <input
            type="checkbox"
            id="number"
            name="number"
            value="number"
            v-model="number"
          />
        </li>
        <br />
        <li class="container">
          <label for="special">!@#$%^*</label>
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
      const capitalChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
      const numbers = "0123456789";
      const specialChars = "!@#$%^&*";
      let allCharacters = [];

      if (this.capital == true) {
        allCharacters.push(capitalChars);
      }
      if (this.lowercase == true) {
        allCharacters.push(lowercaseChars);
      }
      if (this.number == true) {
        allCharacters.push(numbers);
      }
      if (this.special == true) {
        allCharacters.push(specialChars);
      }

      allCharacters = allCharacters.join("");
      let charactersLength = allCharacters.length;

      for (var i = 0; i < this.length; i++) {
        finalResult += allCharacters.charAt(
          Math.floor(Math.random() * charactersLength)
        );
      }
      return (this.password = finalResult);
    },
    async copyToClipboard() {
      if (!navigator.clipboard) return;
      await navigator.clipboard.writeText(this.password);
    },
  },
};
</script>

<style scoped lang="scss">

h1 {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
label {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 30px;
}

li {
  display: flex;
  margin-bottom: 1rem;
  justify-content: space-between;
  border-bottom: 1px solid rgb(70, 70, 70);
}

img {
  max-width: 2rem;
  max-height: 2rem;
}
.angled-gradient-button {
  max-width: 50%;
  max-height: 8rem;
  background-size: 220%;
  box-shadow: 0 0.2em 0.3em rgba(0, 0, 0, 0.15);
  color: #000000;
  background-color: transparent;
  background-position: 100%;
  border: 3px solid #000000;
  text-transform: uppercase;
  padding: 8px 16px;
  border-radius: 3px;
  transition: all 0.2s ease-out;
  font-weight: 900;
  cursor: pointer;
  letter-spacing: 2px;
  background-image: linear-gradient(
    110deg,
    #313131 0%,
    #313131 50%,
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
