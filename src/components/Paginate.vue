<template>
  <span >

  <TableHead :personArray="personArray" />
</span>

  <div class="pagination-row">
    <button
      class="pagination-button"
      :disabled="pageNumber <= 1"
      @click="changePageNumber(pageNumber - 1)"
    >
      Previous
    </button>
    <span v-for="(item, index) in new Array(numberPages)" :key="index">
      <span>
        <button :class="['pagination-button', pageNumber == index + 1 ? 'active' : ''] " @click="changePageNumber(index+1)">{{ index + 1 }}</button>
      </span>
    </span>
    <button
      class="pagination-button "
      :disabled="pageNumber >= numberPages"
      @click="changePageNumber(pageNumber + 1)"
    >
      Next
    </button>
    <slot />
  </div>


</template>

<script>
import TableHead from "./TableHead.vue";
export default {
  name: "Paginate",
  data() {
    return {
      pageNumber: 1,
      perPage: 10,
    };
  },
  computed: {
    numberPages() {
      return Math.ceil(this.totalNumber / this.perPage);
    },
  },
  props: {
    personArray: Array,
    totalNumber: {
      type: Number,
      required: true,
    },

    isEven: false,
  },
  methods: {
      changePageNumber(newPageNumber){
          this.pageNumber = newPageNumber
      },
      async fetchData() {
          const res = await fetch('http://localhost:5000/person');

          const person = await res.json();
          return person
      }
  },
  async created() {
      this.person = await this.fetchData();
  },
  components: {
    TableHead,
  },
};
</script>

<style scoped>
button.page-link {
  display: inline-block;
}
button.page-link {
  font-size: 20px;
  color: #29b3ed;
  font-weight: 500;
}
.offset {
  width: 500px !important;
  margin: 20px auto;
}
li {
  list-style: none;
}
.pagination-button {
  padding: 8px;
  margin: 2px;
  border-radius: 3px;
  font-size: 1rem;
  cursor: pointer;
}
.active {
    border : 2px solid black;
    background:grey;
}
.pagination-row {
  padding: 5px, 0;
}
</style>
