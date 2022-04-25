<template>
  <div class="container_costum">
    <p>
      BOOLFLIX
    </p>
    <form action="">
      <input placeholder="Search" v-model="search" type="text" @keyup="$emit('search', search)">
    </form>
  </div>
</template>

<script>
  export default {
    name: 'HeaderComp',

    data() {
      return {
        search: "",
        
      }
    },
    


  }
</script>

<style scoped lang="scss">
  .container_costum {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    height:60px;
    background:#262626 ;
    border: 1px black solid;
    border-radius: 0 0 10px 10px;

    p {
      font-size: 1.5rem;
      font-weight: bolder;
      color: red;
      margin: auto 15px;
    }

    input {
      margin: 0 15px;
      padding: 0 10px;
      border-radius: 5px;
      background:transparent;
    }
  }
</style>