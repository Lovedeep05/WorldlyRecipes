<script>
  export let recipe;
  console.log(recipe);
</script>


{#if recipe != undefined}
  <div class="main">
  <h1>{recipe["nameOfDish"]}</h1>
  <img src="{recipe["dishImage"]}" alt="dishImage">
  <ol>
  {#each recipe["ingredients"] as line}
    <li>{line}</li>
  {/each}
  </ol>

  <ol>
  {#each recipe["instructions"] as line}
    <li>{line}</li>
  {/each}
  </ol>

  </div>
{/if}


<style>
.main{
  background:skyblue;
  border-radius:15px;
}

img {
    width: 17vw;
		height: 15vw;
    object-fit: cover;
    position: relative;
  }
</style>