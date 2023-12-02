<script>
  import Recipe from "./Recipe.svelte";
  let username="@Velia"
  let image="images/lisaProfilePicture.jpg"
  export let recipes;
  export let users;
</script>

<div class="main">
  <div class="info">
    <h1>{username}</h1>
    <img class="profilePic" src={image} alt="profilePic"/>
  </div>
  <div class="info">
    <h1>Personal information</h1>
    <h2>Email</h2>
    <p>veli@onvenus.com</p>
    <h2>First Name</h2>
    <p>velia</p>
    <h2>Last Name</h2>
    <p>velia</p>
  </div>
  <div class="info">
    <h1>empty char</h1>
    <h2>Posts</h2>
    <p>n</p>
    <h2>Followers</h2>
    <p>n</p>
    <h2>Following</h2>
    <p>n</p>
  </div>
  <div class="posts">
   <h1>recipes</h1>
  </div>
</div>


<style>
  .main{
    padding: 0px;
    border-radius: 10px;
    width: 100%;
    text-align: center;
    background: skyblue;
    display: flex;
  }

  img{
    height:200px;
    width:200px;
    border-radius: 10px
  }

  .backdrop{
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0,0,0,0.8);
  }
</style>