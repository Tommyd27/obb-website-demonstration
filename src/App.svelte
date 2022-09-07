
<script>
	// These values are bound to properties of the video
	let time = 0;
	let tempPovValue = "POV";

	function toggleVideo()
	{
		if (povs[selectedPov].paused)
		{
			povs[selectedPov].play()
		}
		else
		{
			povs[selectedPov].pause()
		}
	}
	function handlePovSubmit()
	{
		let isPaused = povs[selectedPov].paused
		let videoTime = povs[selectedPov].currentTime
		console.log(videoTime)
		
		povs[selectedPov].pause()
		povs[tempPovValue].currentTime = videoTime
		selectedPov = tempPovValue
		
		if (!isPaused)
		{
			povs[selectedPov].play()
		}
		
	}
	function info()
	{
		console.log(selectedPov);
		console.log(povs);
		console.log(tempPovValue);
	}

	let showBoosts = true;
	let players = ["Cam", "Loftzu", "Tom", "Yuri"];


	let povs = {"Cam": "", "Loftzu": "", "Tom": "", "Yuri": "", "Base": "", "Default UI": ""};
	let selectedPov = "Tom";
</script>

<svelte:head>
	<title>Rocket League Object Based Broadcasting Demo</title>
	<meta name="robots" content="noindex nofollow" />
	<html lang="en" />
</svelte:head>
<div>
	<div id = "container" style = "position:relative">
			{#each Object.keys(povs) as pov}
				<div id = "mainVideo" style = "position:absolute; top:0; left:0; z-index: 1; opacity : 1">
					<!-- svelte-ignore a11y-media-has-caption -->
					<video src = "assets/POV {pov}.mp4"
						bind:this = {povs[pov]}
						
						id = "povVideo"
						style = "opacity : {selectedPov == pov ? 1 : 0}"></video>
				</div>
			{/each}
		
		<!--<div class = "playerBoosts" style = "position:absolute; top:0; left:0; z-index: 1; opacity: {showBoosts ? 1 : 0}; z-index: 2; display: grid; grid-template-columns: 1068px 300px; grid-template-rows: 600px auto 30px auto">
			{#each players as player, i}
				<!-- svelte-ignore a11y-media-has-caption 
	 			<video src = "assets/Boost {player}.mp4"
		 			bind:currentTime = {time}
		 			id = "boostVideo"
					style = "padding-bottom:0px; grid-column: {i < 2 ? 1 : 2}; grid-row: {i % 2 == 0 ? 2 : 4}"></video>
 			{/each}
		</div>-->
		<!-- svelte-ignore a11y-media-has-caption -->
		<video src = "assets/Timer.mp4" style = "position:absolute; top: 0; left: 790px; z-index: 3; width: 200px"
			bind:currentTime = {time}></video>
		<div class = "uiContainer" style = "z-index: 3; position:absolute; left: 1750px; top: 0px">
			<select bind:value = {tempPovValue}>
				{#each Object.keys(povs) as povOption}
					<option value = {povOption}>
						{povOption}
					</option>
				{/each}
			</select>
			<button type=submit on:click={handlePovSubmit}>
				Change POV
			</button>
			<button type=submit on:click={toggleVideo}>
				Play/ Pause Video
			</button>
			<button type=submit on:click={info}>
				Current POV
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
