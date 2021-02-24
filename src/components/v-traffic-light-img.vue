<template>
	<div>
		<img 
		:src="require(`../assets/images/${trafficLight}`)"  
		alt="traffic-light" >
	</div>
</template>

<<script>
export default {
	name: 'v-traffic-light',
	data() {
		return {
			trafficLight: 'traffic-light.png'
		}
	}
}
</script>

<style lang="scss" scoped>
	img {
		z-index: 0;
		position: absolute;
		left: 50%;
		top: 44%;
		transform: translate(-50%, -50%);
		margin: 0 auto;
		width: 525px;
		height: 614px;
	}

	@media (max-width: 600px) and (min-height: 460px)   {
		img {
			width: 262.5px;
			height: 307px;
		}
	}



	@media only screen and (min-device-width: 481px) and (max-device-width: 1024px) and (orientation:landscape) {
		img {
			width: 262.5px;
			height: 307px;
		}
	}

		@media (max-width: 568px) and (max-height: 320px)   {
		img {
			width: 131.25px;
			height: 153.5px;
		}
	}


	
</style>