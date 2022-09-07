<script>
	export let name = "cam";
	export let details = 0;
</script>

<div class="boost bg">
	
	<div class="boost" style="width: {details[4]}%"/>
	<h1>{name}</h1>
	<div class = "iconContainers">
		<div class = "iconContainer1">
			<img src = "assets/points.webp" alt = "Points" width = 25/>
			<h2>{details[0]}</h2>
		</div>

		<div class = "iconContainer2">
			<img src = "assets/goals.webp" alt = "Goals" width = 25/>
			<h2>{details[1]}</h2>
		</div>

		<div class = "iconContainer3">
			<img src = "assets/assists.webp" alt = "Shots" width = 25/>
			<h2>{details[3]}</h2>
		</div>

		<div class = "iconContainer4">
			<img src = "assets/saves.webp" alt = "Saves" width = 25/>
			<h2>{details[2]}</h2>
		</div>
	</div>
	
  </div>
  
  <style>
	.boost {
	  grid-column: 1;
	  grid-row: 1;
	  height: 50px;
	  background-color: pink;
	  z-index: 2;
	  
	}
	.bg {
	  width: 300px;
	  background-color: rgb(0, 106, 130);
	  display : grid;
	  margin-bottom: 10px;
	  z-index: 1;
	}
	h1 {
		grid-column: 1;
		grid-row: 1;
		padding-left: 20px;
		font-size: 18px;
		text-align: left;
		/*text-shadow: -2px -2px 0 #000, 2px -2px 0 #000, -2px 2px 0 #000, 2px 2px 0 #000;*/
		margin-top: 1px;
		margin-bottom: -1px;
		z-index: 3;


	}
	h2 {
		font-size: 20px;
		text-align: left;
		
		margin-top: -30px;
		margin-bottom: 30px;
		
		margin-right: 0; /*-165px;*/
		margin-left: 25px;
		z-index: 3;
	}


	.iconContainers {
		display: grid;
		grid-template-columns: 75px 50px 50px 50px;
		margin-top: -30px;
		margin-bottom: 30px;
		z-index: 3;
	}
	.iconContainer1 {
		grid-column: 1;
		grid-row: 1;
		margin-left: 10px;
		margin-right: 10px;
		z-index: 3;
	}
	.iconContainer2 {
		grid-column: 2;
		grid-row: 1;
		z-index: 3;
	}
	.iconContainer3 {
		grid-column: 3;
		grid-row: 1;
		z-index: 3;
	}
	.iconContainer4 {
		grid-column: 4;
		grid-row: 1;
		z-index: 3;
	}


  </style>