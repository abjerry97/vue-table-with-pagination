<template>
  <div class="input-group mb-2">
    <input
      type="text"
      class="form-control"
      placeholder="Search Person"
      v-model="searchName"
    />
    <div class="input-group-append">
    <Button  @click = "searchResults" text="Search"/>
  </div> 
  </div>
</template>     

<script>
import Button from "./Button.vue";
export default {
  name: "SearchBox",
  data() {
    return{
      searchName: ''
    }
  },
  components: {
    Button,
  },
  props: ["value"],
  methods: {
    searchResults(e){
      e.preventDefault();
      if(!this.searchName){
        alert("please enter a name")
        return;
      }

      const searchInput = {
        searchName: this.searchName
      }
      this.$emit('search-input', searchInput)
    }  },
};
</script>