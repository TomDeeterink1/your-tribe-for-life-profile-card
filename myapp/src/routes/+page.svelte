<script>
  import { onMount } from 'svelte'; //import onmount
import { get } from 'svelte/store';

  let person = null; 

  const getapi = async () => {
      const res = await fetch("https://fdnd.directus.app/items/person/14"); //api fetch
      const data = await res.json(); //data fetch
      console.log(data); //console log voor data retrieval
      person = data.data; //verklaar de data aan het persoon person
  }

  // gebruik onmount om de functie uit te voeren
  onMount(() => {
      getapi();
  }); 

</script>


<div class="wrapper">
  <section class="main-section">
      {#if person} 
      <!-- Als person data geladen is, laat dit zien -->
       <div class="lightsaber1"></div>
      <h1>{person.name} {person.surname}</h1> 
      <p>{person.bio}</p>
      <ul class="socials">
          <li><a href="{person.github_handle}">Github</a></li>
          <li><a href="{person.website}">Website</a></li>
      </ul>
      <div class="lightsaber2"></div>
      {:else}
          <!-- Als person data aan het laden is, laat dit zien -->
      <h1>Loading Data...</h1>
      {/if}
  
  </section>
</div>

<style>
 .wrapper{
  width: 100%;
  height: 100vh;
  background: url(foto.jpg);
  object-fit: contain;
  display: flex;
  align-items: center;
  justify-content: center;
      & .main-section{
          background-color: rgba(0, 0, 0, 0.63);
          border-radius: 1em;
          padding: 4em;
          width: 300px;
          color: white;
          transition: ease-out 0.4s;
          transform: matrix3d(0.9958652, -0.0027093, 0, -0.13e-05, -0.019669, 0.704708, 0, -0.0008721, 0, 0, 1, 0, 0, 35, 0, 1);
          & h1 , p , a{
              color: goldenrod;
              font-family:  Helvetica ;
              font-weight: bold;
              word-spacing: 10px;
              text-align: center;
          }
          & .socials{
              list-style-type: none;
              display: flex;
              justify-content: center;
              flex-direction: column;
              gap: 3em;
              align-items: center;
              padding-inline-start: 0px;
          }
          & a{
              position: absolute;
              z-index: 99;
              margin-left: -30px;
              text-align: center;
              text-underline-offset: 2px;
              transition: ease-out 0.2s;
              &:hover{
                  text-underline-offset: 8px;
                  transition: ease-in 0.3s;
              }
          }
          & .lightsaber1{
              box-shadow: 40px 0px 20px  black;
              transition: ease-in 0.4s;
              position: absolute;
              margin-top: -20px;
              content: "";
              height: 10px;
              width: 48px;
              border-radius: 2px;
              background-color: red;
                  &::before{
                      border-radius: 2px;
                  position: fixed;
                  content: "";
                  height: 12px;
                  margin-top: -1px;
                  margin-left: -2px;
                  width: 50px;
                  background-color: rgb(63, 63, 63);
                  box-shadow: inset 0px 0px 5px rgb(19, 19, 19);
                  }
          }
          & .lightsaber2{
              box-shadow: 40px 0px 20px  black;
              border-radius: 2px;
              transition: ease-in 0.4s;
              position: absolute;
              margin-top: 20px;
              content: "";
              height: 10px;
              width: 48px;
              background-color: blue;
              border-radius: 2px;
                  &::before{
                  position: fixed;
                  border-radius: 2px;
                  content: "";
                  height: 12px;
                  width: 50px;
                  margin-top: -1px;
                  margin-left: -2px;
                  background-color: rgb(160, 160, 160);
                  box-shadow: inset 0px 0px 5px rgb(19, 19, 19);
                  }
          }
          &:hover{
              transform: none;
              cursor: pointer;
              & .lightsaber1, .lightsaber2{
              width: 300px;
              transition: ease-in 0.4s;
              }
              & .lightsaber1{
                  box-shadow: 40px 0px 20px  red;
                  transform: rotate(25deg) translateY(92px);
                  
              }
              & .lightsaber2{
                  box-shadow: 40px 0px 20px blue;
                  transform: rotate(-25deg) translateY(-92px);
              }

          }
      }
 }
</style>