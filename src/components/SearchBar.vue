<template>
  <div>
    <form class="example">
      <input type="text" placeholder="Search.." name="search" ref="searchText">
      <button type="submit" v-on:click.prevent='searchTerm()'><i class="fa fa-search"></i></button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  data: function () {
    return {
      searchString: ''
    }
  },
  methods: {
    searchTerm: function () {
      this.searchString = this.$refs.searchText.value;
      this.$emit('termChange', this.searchString)
    }
  }
}
</script>

<style scoped>
  div {
    text-align: "center";
    margin: 20px;
    position: relative;
  }

  * {
  box-sizing: border-box;
}

/* Style the search field */
form.example input[type=text] {
  padding: 10px;
  font-size: 17px;
  border: 1px solid grey;
  float: left;
  width: 80%;
  background: #f1f1f1;
}

/* Style the submit button */
form.example button {
  float: left;
  width: 20%;
  padding: 10px;
  background: #2196F3;
  color: white;
  font-size: 17px;
  border: 1px solid grey;
  border-left: none; /* Prevent double borders */
  cursor: pointer;
}

form.example button:hover {
  background: #0b7dda;
}

/* Clear floats */
form.example::after {
  content: "";
  clear: both;
  display: table;
}
</style>
