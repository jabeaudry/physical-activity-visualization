<template>
	<div class="year-picker-container">
		<div id="year-label" unselectable="on">Year</div>
		<div>
				<svg width="118" height="118" viewBox="0 0 118 118" fill="none" xmlns="http://www.w3.org/2000/svg">
					<g id="date-picker-button">
						<circle id="button-circle-background" cx="59" cy="59" r="59" fill="#161D28"/>
						
						<a id="button-top-container" @click='changeYearUp()'>
							<path id="button-top-circle" d="M105.358 22.5C94.5537 8.79697 77.8042 4.11536e-06 59 2.47145e-06C40.1958 8.27537e-07 23.4463 8.79696 12.6423 22.5L105.358 22.5Z" fill="#161D28"/>
							<path id="button-top-arrow" d="M53.9252 14.652C53.713 14.8749 53.4265 15 53.1279 15C52.8294 15 52.5429 14.8749 52.3307 14.652C52.226 14.5425 52.1428 14.412 52.086 14.268C52.0292 14.1241 52 13.9696 52 13.8136C52 13.6575 52.0292 13.503 52.086 13.3591C52.1428 13.2152 52.226 13.0846 52.3307 12.9752L58.702 6.34752C58.9146 6.12485 59.2013 6.00002 59.5 6.00002C59.7987 6.00002 60.0854 6.12485 60.298 6.34752L66.6693 12.9752C66.774 13.0846 66.8572 13.2152 66.914 13.3591C66.9708 13.503 67 13.6575 67 13.8136C67 13.9696 66.9708 14.1241 66.914 14.268C66.8572 14.412 66.774 14.5425 66.6693 14.652C66.4566 14.8746 66.1699 14.9995 65.8712 14.9995C65.5725 14.9995 65.2858 14.8746 65.0732 14.652L59.4976 9.21661L53.9252 14.652Z" fill="#F4EBE8"/>
						</a>
						<a id="button-bottom-container" @click='changeYearDown()'>
							<path id="button-bottom-circle" d="M12.6423 95.5C23.4463 109.203 40.1958 118 59 118C77.8042 118 94.5537 109.203 105.358 95.5H12.6423Z" fill="#161D28"/>
							<path id="button-bottom-arrow" d="M65.0748 103.348C65.287 103.125 65.5735 103 65.8721 103C66.1706 103 66.4571 103.125 66.6693 103.348C66.774 103.458 66.8572 103.588 66.914 103.732C66.9708 103.876 67 104.03 67 104.186C67 104.343 66.9708 104.497 66.914 104.641C66.8572 104.785 66.774 104.915 66.6693 105.025L60.298 111.653C60.0854 111.875 59.7987 112 59.5 112C59.2013 112 58.9146 111.875 58.702 111.653L52.3307 105.025C52.226 104.915 52.1428 104.785 52.086 104.641C52.0292 104.497 52 104.343 52 104.186C52 104.03 52.0292 103.876 52.086 103.732C52.1428 103.588 52.226 103.458 52.3307 103.348C52.5434 103.125 52.8301 103.001 53.1288 103.001C53.4275 103.001 53.7142 103.125 53.9268 103.348L59.5024 108.783L65.0748 103.348Z" fill="#F4EBE8"/>
						</a>
						
						
						<text id="year-selected"  unselectable="on" dominant-baseline="middle" text-anchor="middle" x="50%" y="50%" >{{currentYear}}</text>
					</g>
				</svg>
		</div>
	</div>
</template>

<script>


export default {
	name: 'year-picker',
	props: {
		//receives the set of years to pick from Activities.vue through App.vue
		currentYear: Number
	},
	methods: {
		changeYearUp(){
			this.$emit('changeYearUp')
		},
		changeYearDown(){
			this.$emit('changeYearDown')
		}
	}
}
// $(function() {
//   $('#button-bottom-circle').hover(function() {
//     $('#button-top-circle').css('fill', '#212A39');
//   }, function() {
//     // on mouseout, reset the background colour
//     $('#button-top-circle').css('fill', '#161D28');
//   });
// });
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Open+Sans&family=Roboto:wght@100;300&display=swap');

	svg, svg * {
		pointer-events: visible;
	}
	.year-picker-container{
		position: fixed;
		display: flex;
		flex-direction: column;
		top: 30vh;
		left: 4vw;
		z-index: 10;
		max-width: 20%;
	}
	#year-label{
		color: #F4EBE8;
		font-size: 2vw;
		font-family: 'Roboto', sans-serif;
		padding-bottom: 15%;
		width: 100%;
		text-align: center;
		
		//unselectable
		-webkit-user-select: none; /* Safari */        
		-moz-user-select: none; /* Firefox */
		-ms-user-select: none; /* IE10+/Edge */
		user-select: none; /* Standard */
	}

	//default button styling hover
	#date-picker-button:hover{
		a #button-top-circle,a #button-bottom-circle{
			fill: #212A39;
			transition: fill 0.3s ease;
		}
		a #button-top-arrow,a #button-bottom-arrow{
			fill: #F4EBE8;
			transition: fill 0.3s ease;
		}
		#button-circle-background{
			fill: #212A39;
			transition: fill 0.3s ease;
		} 
	}

	//date selecting button up button hover
	#button-top-container:hover {
		#button-top-circle {
			fill: #F4EBE8!important;
			transition: fill 0.2s ease;
		}
		#button-top-arrow {
			fill: #212A39!important;
			transition: fill 0.2s ease;
		}
	}

	//date selecting button down button hover
	#button-bottom-container:hover {
		#button-bottom-circle {
			fill: #F4EBE8!important;
			transition: fill 0.2s ease;
		}
		#button-bottom-arrow {
			fill: #212A39!important;
			transition: fill 0.2s ease;
		}
	}
	
	#year-selected{
		fill: #F4EBE8;
		font-size: 2vw;
		font-family: 'Roboto', sans-serif;
		//unselectable
		-webkit-user-select: none; /* Safari */        
		-moz-user-select: none; /* Firefox */
		-ms-user-select: none; /* IE10+/Edge */
		user-select: none; /* Standard */
	}
</style>