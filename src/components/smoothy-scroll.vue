<template>
	<div class="smoothy" @scroll='handleScroll'>
		<div
			class="smoothy-item" 
			v-for="(item, index) in items"
			:style="{transform: 'skewY('+ skewing +'deg)', transition: skewBackSpeed+'ms'}">
			{{index}}
		</div>
	</div>
</template>

<script>
export default {

  name: 'smoothy-scroll',

  data () {
    return {
    	scrollNow: 0,
    	scrollNew: 0,
    	skewing: 0,
    	maxSkew: 3,
    	skewBackSpeed: 0,
    	isScrolling: false,
    	items: [
    	{
    		"id" : 1,
    	},
    	{
    		"id" : 2,
    	},
    	{
    		"id" : 3,
    	},
    	{
    		"id" : 4,
    	},
    	{
    		"id" : 5,
    	},
    	{
    		"id" : 5,
    	},
    	{
    		"id" : 5,
    	},
    	{
    		"id" : 5,
    	},
    	{
    		"id" : 5,
    	},    	    	    	    	    	    	    	    	
    	],
    }
  },
  methods: {
  	handleScroll(e) {
  		clearTimeout(this.isScrolling)
  		this.skewBackSpeed = 0
  		this.scrollNow = this.scrollNew
  		this.scrollNew = e.target.scrollTop
  		this.scrollNew > this.scrollNow ? 
  			window.requestAnimationFrame(this.toSkewingDown) : window.requestAnimationFrame(this.toSkewingUp)
  		this.isScrolling = setTimeout(()=>{
  			this.skewBackSpeed = 888
  			this.skewing = 0
  		}, 50)
  	},
  	toSkewingDown() {
  		if(this.skewing < this.maxSkew){
  			this.skewing += 0.07
  		} else {
  			this.skewing = this.maxSkew
  		}  		
  	},
  	toSkewingUp() {
  		if(this.skewing > -this.maxSkew){
  			this.skewing -= 0.07
  		} else {
  			this.skewing = -this.maxSkew
  		}  	
  	},  	
  },
  mounted() {
  	console.log('mounted')
  },
  beforeUpdate() {

  },
  updated() {
  }
}
</script>

<style lang="scss" scoped>
.smoothy{
	position: relative;
	width: 100%;
	height: 100%;
	padding: 0 5%;
	overflow: scroll;
	display: flex;
	flex-direction: column;
	align-items: center;
}
.smoothy-item{
	position: relative;
	flex: 1 0 auto;
	width: 60%;
	height: 80%;
	margin: 5% 0;
	font-size: 15em;
	display: flex;
	justify-content: center;
	align-items: center;
	background-color: violet;
}
</style>