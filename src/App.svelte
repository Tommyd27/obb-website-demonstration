
<script lang="ts">
	/* eslint-disable jsx-a11y/media-has-caption */
	// These values are bound to properties of the video
	let time = 0;
	let paused = false;
	let tempPovValue = "POV";
	let mainVideo;

	/*function handlePovSubmit()
	{
		let currentTime = time;
		let currentlyPaused = paused;

		console.log("currentTime: ", currentTime);
		console.log("currentlypaused: ", currentlyPaused);
		console.log("time ", time)
		console.log("paused ", paused);
		console.log("");
		pov = tempPovValue;
		console.log("currentTime: ", currentTime);
		console.log("currentlypaused: ", currentlyPaused);
		console.log("time ", time)
		console.log("paused ", paused);
		console.log("");
		
		//time = currentTime;
		//paused = currentlyPaused;
		console.log("currentTime: ", currentTime);
		console.log("currentlypaused: ", currentlyPaused);
		console.log("time ", time)
		console.log("paused ", paused);
		console.log("");

		mainVideo.play();
		


	}*/
	function handlePovSubmit()
	{
		/*let currentTime = time;
		let currentPaused = paused;
		pov = tempPovValue;
		time = currentTime;
		paused = currentPaused;*/
		console.log(paused);
		paused = false;
		time = 200;
		console.log(paused);
	}


	let showBoosts = true;
	let players = ["Cam", "Loftzu", "Tom", "Yuri"];


	let povs = ["Cam", "Loftzu", "Tom", "Yuri", "Base", "Default UI"];
	let pov = povs[1];
</script>

<svelte:head>
	<title>Rocket League Object Based Broadcasting Demo</title>
	<meta name="robots" content="noindex nofollow" />
	<html lang="en" />
</svelte:head>
<div>
	<div id = "container" style = "position:relative">
		<div id = "mainVideo" style = "position:absolute; top:0; left:0; z-index: 1; opacity : 1">
			<video src = "assets/POV {pov}.mp4"
				bind:currentTime = {time}
				bind:paused= {paused}
				bind:this = {mainVideo}
				id = "povVideo"></video>
		</div>"
		
		<div class = "playerBoosts" style = "opacity: {showBoosts ? 1 : 0}; z-index: 2; display: grid; grid-template-columns: 1428px 300px; grid-template-rows: 600px auto 30px auto">
			{#each players as player, i}
	 			<video src = "assets/Boost {player}.mp4"
		 			bind:currentTime = {time}
		 			id = "boostVideo"
					style = "padding-bottom:0px; grid-column: {i < 2 ? 1 : 2}; grid-row: {i % 2 == 0 ? 2 : 4}"></video>
 			{/each}
		</div>
		<video src = "assets/Timer.mp4" style = "position:absolute; top: 0; left: 790px; z-index: 3; width: 200px"
			bind:currentTime = {time}></video>
		<div class = "uiContainer" style = "z-index: 3; position:absolute; left: 1750px; top: 0px">
			<select bind:value = {tempPovValue}>
				{#each povs as povOption}
					<option value = {povOption}>
						{povOption}
					</option>
				{/each}
			</select>
			<button type=submit on:click={handlePovSubmit}>
				Change POV
			</button>
		</div>
		
		
 	</div>
	



	
</div>
<style>
	#boostVideo
	{
		width: 270px;
		height: 100%;
		object-fit: cover;
	}
	#povVideo
	{
		width: 90%;
	}
	
</style>
