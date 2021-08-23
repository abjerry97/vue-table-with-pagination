<template>
<div>
    <h1> {{data.value}} </h1>
    <Button @btnMethod = "getUser()" text="Add Random Person"/>
  <SearchBox v-model="content"/>
  <TableHead :personArray="personArray" />
  </div>   
</template>

<script>

 import TableHead from "../components/TableHead.vue";
 import Button from "../components/Button.vue";
 import SearchBox from "../components/SearchBox";
export default {
  name: "HomeScreen",
  components: {
  TableHead,
   Button,
    SearchBox,
 },
  props: {
    value: ""
}
,
 methods: {
    onClick() {
      this.$emit('getUser()')
    },
  },
}
</script>