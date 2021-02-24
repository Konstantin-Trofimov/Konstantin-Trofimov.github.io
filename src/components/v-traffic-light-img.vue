<template>
	<div>
		<img 
		class="traffic-light-img"
		:src="require(`../assets/images/${trafficLight}`)"  
		alt="traffic-light" >
	</div>
</template>

<script>

export default {
	name: 'v-traffic-light',
	data() {
		return {
			trafficLight: 'traffic-light.png'
		}
	}
}
</script>

<style lang="scss">
	.traffic-light-img {
		z-index: 0;
		position: absolute;
		left: 50%;
		top: 44%;
		transform: translate(-50%, -50%);
		margin: 0 auto;
		width: 525px;
		height: 614px;
	}	
</style>