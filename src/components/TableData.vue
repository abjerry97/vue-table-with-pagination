<template>

        <td>{{ id }}</td>
        <td>{{ firstName }}</td>
        <td>{{ lastName }}</td>
        <td>{{ gender }}</td>
        <td>{{ email }}</td> 
        
</template>

<script>

export default {
  name: "TableData",
  props: {
    pageNumber: Number,
    id: Number,
    firstName: String,
    lastName: String,
    gender: String,
    email: String,
    isEven: false,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  body {
    font-family: Arial, Verdana, sans-serif;
    font-size: 90%;
    color: #666;
    background-color: #f8f8f8;
}
table {
  border-spacing: 0px;
}
td {
  padding: 5px 30px 5px 10px;
  border-spacing: 0px;
  font-size: 90%;
  margin: 0px;
}

td {
  text-align: left;
  background-color: #e0e9f0;
  border-top: 1px solid #f1f8fe;
  border-bottom: 1px solid #cbd2d8;
  border-right: 1px solid #cbd2d8;
}

td {
  text-shadow: 1px 1px 1px #fff;
}
tr.even td,
tr.even th {
  background-color: #e8eff5;
}
</style>
