<script>
  const backgroungPhrases=["Spice up your life, one dish at a time!","Where flavors dance and recipes come alive.","Savor the taste of homemade goodness.","From kitchen chaos to culinary triumphs.","Cooking up delicious memories.","Elevate your meals, ignite your passion.","Where every recipe tells a story.","Unleash your inner chef.","Creating magic, one recipe at a time.","Turning ordinary ingredients into extraordinary meals."]

  export let data;
  import Category from "./Category.svelte";
  import Recipe from "./Recipe.svelte";
</script>

<div class="img1">
<img src="https://images.pexels.com/photos/326281/pexels-photo-326281.jpeg" alt="backgroundPicture" class=bgPic>
<p class="catchphrase">{backgroungPhrases[Math.floor(Math.random() * (backgroungPhrases.length - 0) + 0)]}</p>
</div>

<Category categories={data["Categories"]}/>
<Recipe recipes={data["Recipes"]}/>  




<style>
.bgPic{
  width: 100%;
  height:500px;
  object-fit: cover;
}

.img1{
  position: relative;
  text-align: center;
  color: white;
}

.catchphrase{
  position: absolute;
  top: 40%;
  left: 70%;
  transform: translate(-50%, -50%);
  font-size:300%;
  font-family: "Georgia";
  background-color:black;
  background-color:rgba(0,0,0,0.3);
  border-radius: 15px;
  padding: 10px;
  width:40%;
}
</style>