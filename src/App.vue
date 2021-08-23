<template>
  <div class="row  button">
  <Button @btnMethod = "getUser()" text="Add Random Person"/>
  
  </div>
   <main>
     <div> 
      
  <div class="row paginate">
  <paginate :personArray="personArray" :totalNumber="personArray.length" /> 
  </div>  
  </div>
 </main>  
</template>

<script>


var temp_id = 1
var temp_pageNumber = 1
import HomeScreen from "./screens/HomeScreen.vue";
import Button from "./components/Button.vue";
import Header from "./components/Header.vue";
import SearchBox from "./components/SearchBox";
import Paginate from './components/Paginate.vue';
export default {
  name: "App",
  components: {
    HomeScreen,
    Button,
    Header,
    SearchBox,
    Paginate,
    SearchBox,
  },
  data() {
    return {
       personArray: [
        ],
        personArrayWithPagination:[

        ],
        value: '',
        
    };
  },
  methods: {
    async  getUser() {
    const res = await fetch('https://randomuser.me/api');
         const { results } = await res.json();
      this.personArray = [...this.personArray,

     {
         
         firstName: results[0].name.first,
        lastName: results[0].name.last,
        email: results[0].email,
         gender: results[0].gender,
         id:temp_id++,
         pageNumber: (temp_id/10 >= 1 && temp_id %10 ===0 ? temp_pageNumber++ : temp_pageNumber) 
         
       }
      ];
    },
    searchInput(personArray){
      
    }
    
    
  },
};
</script>

<style>
html{
  font-size: 62.5%; /* 16px x 62.5% = 10px = 1rem */ 
  box-sizing: border-box;
}
body{
  margin: 0;
  height: 100vh;
  font-size: 1.6rem;
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
#app {
  height: 100%;
}

/* layout */
.grid-container {
  display: grid;
    grid-template-areas: 
        'header'
        'main'
        'footer';

    grid-template-columns: 1fr;
    grid-template-rows: 5rem 1fr 5rem;
    height: 100%;
}

header{
  grid-area: header;
  background-color: #203040;
}
main{
  grid-area: main;
  padding: 1rem;
  height: 100%;
  display: flex;
  align-items: center;
  margin-left: 50rem;
}
footer{
  grid-area: footer;
  background-color: #203040;
  color: #ffffff;
}
.row {
  display: grid;
}
.search{
  width: 50%;
  margin-left: 70%;
  height: 5rem;
  padding: 0%;
}
.button{
  width: 10%;
  margin-left: 40%;
  margin-top: 5rem;
  margin-bottom: 2rem;
  display: inline-block;
  color: #fff;
  cursor: pointer;
  text-decoration: none;
  font-family: inherit;
}

</style>
