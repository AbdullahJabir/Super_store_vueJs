<template>
	 <ul class="list-group" >
      <li class="list-group-item" v-for="(item,index) in items" :key="index">
      	<span class="item-name">{{item.title}}</span>
      	<span class="item-price float-right">{{item.price}}</span>
      	<button class="btn btn-sm btn-danger" @click="removeItem(index)">-</button>
      </li>
       <li class="list-group-item" >Total - ${{totalPrice}}</li>
      
    </ul>
</template>
<script>


export default {
	props:['items'],
	
	methods:{
		removeItem(index){
			this.$emit('itemRemove',index)
		}
	},
	computed:{
		totalPrice(){
			var total=0
			this.items.forEach(item=>{
				total += parseFloat(item.price)
			})
			return total
		}
	}
	
  
}
</script>