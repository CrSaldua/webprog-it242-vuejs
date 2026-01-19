<template>
  <div clas="Durian">
    <h2>{{ name }}</h2>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'Durian and mangosteen',   
      message: 'I like Durian and mangosteen'
    }
  }
};
</script>

<style>
  .Durian {
    border: dashed black 1px;
    display: inline-block;
    margin: 10px;
    padding: 10px;
    background-color: yellow;
  }
  </style>