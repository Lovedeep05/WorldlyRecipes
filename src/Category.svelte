<script>
  export let categories
  </script>


<div class="slider">
	{#each categories as category}
		<div class="glass-box">
			<div class="glass-icon">
				<img src="{category["img"]}" alt="categoryImg">
      </div>
			<p class="titolo">{category["name"]}</p>
			<p>add description</p>
		</div>
	{/each}
</div>

<style>

	
	.glass-box {
		background-color:#FF0000;
    border-radius:3rem;
		padding: 0;
		width: 17vw;
		height: 25vw;
		scroll-snap-align: start;
		text-align: center;
		position: relative;
		margin:5px;
	}

	.glass-icon {
		border-radius: 30px 30px 0px 0px;
		width: 17vw;
		height: 15vw;
		overflow: hidden;
	}

	img {
    width: 17vw;
		height: 15vw;
    object-fit: cover;
    position: relative;
  }

	.titolo {
  order:1;
  font-weight: bold;
  text-align: center;
  color: black;
}
  .slider {
		font-family: sans-serif;
		scroll-snap-type: x mandatory;	
		display: flex;
		-webkit-overflow-scrolling: touch;
		overflow-x: scroll;
	}
</style>

