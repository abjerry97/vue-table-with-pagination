<template>
 <div id="app">
    <table >
        <tr class="head">
            <th>id</th>
            <th>First Name</th>
            <th>Last Name</th>
            <th>Sex</th>
            <th>Email Address</th>

        </tr>
        <tr :key="person.id"  :class="[person.id % 2 ===0 ? 'even' : '']" v-for="person in personArray.slice(0,10) ">
        <TableData :pageNumber="person.pageNumber" :id="person.id" :firstName="person.firstName" :lastName="person.lastName"  :gender="person.gender" :email="person.email"/>
        </tr>
    </table>
</div>
</template>

<script>
import TableData from './TableData.vue'

export default {
  name: 'TableHead',
  props: {
    personArray: Array,
    isEven: false,
    totalNumber: {
      type: Number,
      required: true,
    },
  },
  
   components: {
    TableData
  },
   methods: {
      changePageNumber(newPageNumber){
          this.pageNumber = newPageNumber
      },
  },
}
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
th {
    padding: 5px 30px 5px 10px;
    border-spacing: 0px;
    font-size: 90%;
    margin: 0px;
}

th {
    text-align: left;
    background-color: #e0e9f0;
    border-top: 1px solid #f1f8fe;
    border-bottom: 1px solid #cbd2d8;
    border-right: 1px solid #cbd2d8;
}

tr.head th {
    color: #fff;
    background-color: #90b4d6;
    border-bottom: 2px solid #547ca0 ;
    border-right: 1px solid #749abe;
    border-top: 1px solid #90b4d6;
    text-align: center;
    text-shadow: -1px -1px 1px #666;
    letter-spacing: 0.15rem;
}
  tr.even th {
    background-color: #e8eff5;
}
tr.head th:first-child {
    -webkit-border-top-left-radius: 5px;
    -moz-border-radius-topleft: 5px;
    border-top-left-radius: 5px;
}

tr.head th:last-child {
    -webkit-border-top-right-radius: 5px;
    -moz-border-radius-topright: 5px;
    border-top-right-radius: 5px;
}
.even  {
  background-color: #e8eff5;
}
</style>
