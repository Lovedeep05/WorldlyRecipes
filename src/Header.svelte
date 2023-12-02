<script>
  let name="Velia"
  let image="images/lisaProfilePicture.jpg"

  export let viewProfile = false;


  const setTrue = ()=>{
    viewProfile=!viewProfile;
    console.log("viewProfile:" +viewProfile)
  }

</script>


<div class="header flexbox">
  <img class="logo" src="images/logo.png" alt="logo"/>
  <h1>Worldly Recipes</h1>

  <div class="align-right flexbox">
    <a href="instagram.com" >RECIPES</a>
    <div class="divider"></div>
    <a href="instagram.com" >HOLIDAY</a>
    <div class="divider"></div>
    <a href="instagram.com" >INGREDIENTS</a>
    <div class="divider"></div>
    <a href="instagram.com" >ABOUT US</a>
    <div class="divider"></div>
  </div>
  <p on:click={()=> setTrue() }>{name}</p>
  <img class="profilePic" src={image} alt="profilePic" on:click={()=> setTrue() }/>
  <button class="button-5" role="button">LOGIN</button>
  <button class="button-5" role="button">&#x1F50E;&#xFE0E;</button>
</div>


<style>
.header{
  background-color: lightblue;
  height: 100px;
  width: 100%;
}
.flexbox{
  display: flex;
  align-items: center;
}

a{
  color: black;
  text-decoration: none;
}
a:hover {
      text-decoration: underline;
}



.logo{
  height:70px;
  width:70px;
  margin:15px;
}
.profilePic{
  height:50px;
  width:50px;
  margin:15px;
  border-radius: 10px
}



.align-right{
  margin-left: auto;
}

.divider {
  border-left: 2px solid black;
  height: 25px;
  margin:5px
}


.button-5 {
  align-items: center;
  background-clip: padding-box;
  background-color: #FF0000;
  border: 1px solid transparent;
  border-radius: 0.8rem;
  box-shadow: rgba(0, 0, 0, 0.02) 0 1px 3px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-flex;
  font-family: system-ui,-apple-system,system-ui,"Helvetica Neue",Helvetica,Arial,sans-serif;
  font-size: 16px;
  font-weight: 600;
  justify-content: center;
  line-height: 1.25;
  margin: 0;
  min-height: 3rem;
  padding: calc(.875rem - 1px) calc(1.5rem - 1px);
  position: relative;
  text-decoration: none;
  transition: all 250ms;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: baseline;
  width: auto;
}

.button-5:hover,
.button-5:focus {
  background-color: #FF3333;
  box-shadow: rgba(0, 0, 0, 0.1) 0 4px 12px;
}

.button-5:hover {
  transform: translateY(-1px);
}

.button-5:active {
  background-color: #B00000;
  box-shadow: rgba(0, 0, 0, .06) 0 2px 4px;
  transform: translateY(0);
}
</style>