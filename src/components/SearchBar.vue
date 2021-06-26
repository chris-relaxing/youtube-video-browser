<template>
  <div>
    <!-- <input v-on:input="onInput"/> -->
    <!-- Alternative syntax using @ symbol: -->
    <input @input="onInput"/>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onInput: function (event) {
      // console.log(event.target.value);
      this.$emit('termChange', event.target.value)
    }
  }
}
</script>

<style scoped>
  input {
    height: 35px;
    width: 100%;
    font-size: 26px;
  }

  div {
    text-align: "center";
    margin: 20px;
    position: relative;
  }
</style>
