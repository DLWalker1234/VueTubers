<template>
    <div class="SearchContainer">
        <input id="input" placeholder="Search... YouTube" v-on:input="onInput" />
    </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
      onInput: function(event) {
        this.$emit('newSearch', event.target.value);
    }
  }  
};
</script>

<style>

.SearchContainer {
    display: flex;
    justify-content: center;
    background-color: #ccc;
}

#input {
    width: 50%;
    height: 25px;
    border: 2px solid #ccc;
    border-radius: 5px;
    padding-left: 10px;
}

#input:hover {
    border-color: navy;
}


</style>
