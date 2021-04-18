<template>
  <div class="hello">
     <div class="left">
        <h1> {{ title }} </h1>
        <form @submit.prevent="addLink">
          <input type="text" placeholder="Add a link" class="link-input" v-model="newLink"/>
        </form>
        <ul>
          <li v-for="(link,index) in links" :key="index"> {{link}}
             <button @click="removeLinks(index)" class="rm">Remove</button> 
          </li>
        </ul>
        <button @click="deleteAll">remove all links</button>
     </div>
     <div class="right">
        <stats/>
     </div>
  </div>
</template>

<script>
import Stats from './Stats'
import {mapState, mapMutations, mapActions} from 'vuex';
export default {
  name: 'HelloWorld',
  components: {
    Stats,
  },
  data() {
    return {
      newLink:''
    }
  },
  computed: {
    ...mapState([
      'title','links'
    ]),
  },
  methods: {
    ...mapMutations([
      'ADD_LINK'
    ]),
    ...mapActions([
      'removeLink','removeAllLinks'
    ]),
    addLink: function() {
      this.ADD_LINK(this.newLink);
      this.newLink="";
    },
    removeLinks: function(link) {
      this.removeLink(link);
    },
    deleteAll: function() {
      this.removeAllLinks();
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
html, #app, .home {
    height: 100%;
  }
  body {
    background-color: #F4F4F4;
    margin: 0;
    height: 100%;
  }

  .hello {
    display: grid;
    grid-template-columns: repeat(2, 50%);
    grid-template-rows: 100%;
    grid-template-areas:
      "left right";
    height: 100%;
  }

  .left, .right {
    padding: 30px;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }
  ul li {
    padding: 20px;
    background: white;
    margin-bottom: 8px;
  }

  .right {
    grid-area: right;
    background-color: #E9E9E9;
  }
  input {
    border: none;
    padding: 20px;
    width: calc(100% - 40px);
    box-shadow: 0 5px 5px lightgrey;
    margin-bottom: 50px;
    outline: none;
  }
  .rm {
    float: right;
    text-transform: uppercase;
    font-size: .8em;
    background: #f9d0e3;
    border: none;
    padding: 5px;
    color: #ff0076;
    cursor:pointer;
  }
  /* button {
    padding: 10px;
    margin-top: 30px;
    width: 100%;
    background: none;
    border: 1px solid lightgray;
    outline: 0;
    cursor: pointer;
} */
</style>
