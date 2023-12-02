<script>
  import Header from './Header.svelte';
  import HomePage from './HomePage.svelte';
  
  import Footer from "./Footer.svelte";
  import Profile from "./Profile.svelte";
  import Login from "./Login.svelte";
  import Signup from "./Signup.svelte";


  let data;
  async function getData(){
    const response = await fetch('https://raw.githubusercontent.com/Lovedeep05/svelteDataset-Assets/main/dataset.json?token=GHSAT0AAAAAACKY3BCVH7OQON5UOORAMLH2ZLCPINQ');
    let data = await response.json();
    console.log(data)
    if (response.ok) {
			return data;
		} else {
			throw new Error(text);
		}
  }
  data = getData();


  let viewProfile = true;
  let viewHomePage = true;
  let viewLoginPage = true;
  let viewSignupPage = true;


</script>

<Header bind:viewProfile={viewProfile}/>

{#await getData()}
	<p>Fetching resources</p>
{:then data}
  {#if viewHomePage}
    <HomePage data={data}/>
  {/if}
  {#if viewProfile}
    <Profile recipes={data["Recipes"]} users={data["Users"]}/>
  {/if}
  {#if viewHomePage}
    <Login data={data}/>
  {/if}
  {#if viewSignupPage}
    <Signup data={data}/>
  {/if}
{:catch error}
	<p>{error.message}</p>
{/await}
<Footer/>
<main>
</main>
<style>
</style>