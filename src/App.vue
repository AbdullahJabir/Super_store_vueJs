<template>
  <div id="app">
  <navbar @search="search"></navbar>

<div class="container">
<div class="row">
  <div class="col-sm-10">
    <cart @newItemAdded="addCartItem" :items="items"></cart>
  </div>

  <div class="col-sm-2">
   <inventory @itemRemove="RemoveItem" :items="cart"></inventory>
  </div>
</div>
  </div>
  </div>
</template>

<script>

import Navbar from './components/Navbar'
import Cart from './components/Cart'
import Inventory from './components/Inventory'
import data from './data.js'
export default {
  components:{
   navbar: Navbar,
    inventory:Inventory,
    cart:Cart

  },
  data(){
    return{
      items:[],
      cart:[
          ]
    }
  },
  methods:{
    search(keyword){
     this.items= data.filter(item=>{
        return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1
      })
    },
    addCartItem(item){
      this.cart.push(item)
    },
    RemoveItem(index){
      this.cart.splice(index,1)
    }
  },
  mounted(){
    this.items=data
    /*console.log(data);*/
  }
  
}
</script>
<style>
  .container{
    padding-top:5px;
  }
</style>


