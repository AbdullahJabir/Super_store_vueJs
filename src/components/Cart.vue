<template>
	    <div class="row">
    <!-- <div class="card" style="width: 18rem;" v-for="(item,index) in items" :key="index">
  <img :src="item.photo" class="card-img-top" alt="...">
  <div class="card-body">
  	<h5 class="card-title">{{item.title}}</h5>
    <p class="card-text">{{item.price}}</p>
    <a href="#" class="btn btn-primary">+ Add</a>
  </div>
</div> -->
<div class="card" style="width: 18rem;" v-for="(item,index) in items" :key="index">
  <img :src="item.photo" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{item.title}}</h5>
    <p class="card-text">{{item.price}}</p>
    <a @click="addToCart(item)" class="btn btn-primary">+ Add</a>
  </div>
</div>

    </div>
</template>
<script>


export default {
  props:['items'],
  methods:
	{
		addToCart(item){
			this.$emit('newItemAdded',item)
		}
	}
}
</script>