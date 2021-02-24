<template>
	<div 
	id="app"
	:style="{'background-image': 'url(' + require(`@/assets/images/cartoon-street${backgroundNumber}.jpg` ) + ')'}"
	>
		<v-traffic-light-img />
		<router-view/>
		
	</div>
</template>

<script>
	import vTrafficLightImg from '@/components//v-traffic-light-img'
	export default {
		mounted () {
			if (this.$route.path == '/') {
				this.$router.push('yellow')
			}
		},
		components: {
			vTrafficLightImg
		},
		data() {
			return {
				wrapper: {
					backgroundImage: '@/assets/images/cartoon-street.jpg' 
				},
				backgroundNumber: null
			}
		},
		created() {
			const randomInteger = (min, max) => {
				let rand = min - 0.5 + Math.random() * (max - min + 1);
				return Math.round(rand);
			}
			this.backgroundNumber = randomInteger(1, 4)
		}
	}	
</script>

<style lang="scss">
	@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@600&display=swap');

	#app {
		font-family: 'Roboto Mono', monospace;
		height: 100%;
		z-index: -1;
		background-size: cover;
		background-repeat: no-repeat;
		background-position: center;
	}

	body {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}

	.v-lamp {
		margin-top: 87px;
		position: absolute;
		left: 50%;
		top: 44%;
		transform: translate(-50%, -50%);
		height: 700px;
		display: grid;
		grid-template-rows: repeat(3, 184px) 130px;
		align-content: center;
		align-items: center;
	}

	.lamp {
		z-index: 3;
		width: 8.5rem;
		height: 8.5rem;
		margin: 0 auto;
		border: 2px solid #aeaeae;
		border-radius: 50%;

		&_green {
			background: radial-gradient(circle, rgba(255,255,255,1) 11%, rgba(15,247,17,1) 80%);
			filter: blur(.5rem);	
		}

		&_red {
			background: radial-gradient(circle, rgba(255,255,255,1) 11%, rgba(219,20,20,1) 82%);
			filter: blur(.5rem);
		}

		&_yellow {
			background: radial-gradient(circle, rgba(255,255,255,1) 11%, rgba(251,255,0,1) 80%);
			filter: blur(.5rem);
		}

		&_dim {
			opacity: .4;
			filter: none
		}
	}

	.blink {
		animation-name: blinker;
		animation-iteration-count: infinite;
		animation-timing-function: cubic-bezier(1.0,0,0,1.0);
		animation-duration: 1s;
		-webkit-animation-name: blinker;
		-webkit-animation-iteration-count: infinite;
		-webkit-animation-timing-function: cubic-bezier(1.0,0,0,1.0);
		-webkit-animation-duration: 1s;
	}
		
	@keyframes blinker {
		from { opacity: 1.0; }
		to { opacity: 0.0; }
	}
	
	@media (max-width: 600px) and (max-height: 735) {
		.lamp {
			width: 4.2rem;
			height: 4.2rem;
		}

		.v-lamp {
			margin-top: 77px;
			grid-template-rows: repeat(3, 92px) 130px;
		}
	}

	@media (max-width: 600px) and (min-height: 460px) {
		.lamp {
			width: 4.2rem;
			height: 4.2rem;
		}

		.v-lamp {
			margin-top: 77px;
			grid-template-rows: repeat(3, 92px) 130px;
		}
	}


	@media only screen and (min-device-width: 481px) and (max-device-width: 1024px) and (orientation:landscape)  {

		.lamp {
			width: 4.2rem;
			height: 4.2rem;
		}

		.v-lamp {
			margin-top: 77px;
			grid-template-rows: repeat(3, 92px) 130px;
		}

		.v-timer {
			margin-top: -4rem !important;
		}
	}

	@media (max-width: 568px) and (max-height: 320px)   {
		.lamp {
			width: 2.1rem;
			height: 2.1rem;
		}

		.v-lamp {
			margin-top: 70.5px;
			grid-template-rows: repeat(3, 46px) 130px;
			border: 1px solid #aeaeae;
		}
	}

</style>
