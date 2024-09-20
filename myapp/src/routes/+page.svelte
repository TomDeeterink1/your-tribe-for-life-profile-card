<script>
  import { onMount } from "svelte"; //import onmount
  import { get } from "svelte/store";

  let person = null;

  const getapi = async () => {
    const res = await fetch("https://fdnd.directus.app/items/person/14"); //api fetch
    const data = await res.json(); //data fetch
    console.log(data); //console log voor data retrieval
    person = data.data; //verklaar de data aan het persoon person
  };

  // gebruik onmount om de functie uit te voeren
  onMount(() => {
    getapi();
  });
</script>

<div class="wrapper">
  <section class="main-section">
    {#if person}
      <!-- Als person data geladen is, laat dit zien -->
      <img src={person.avatar} width="200px" height="240px" />
      <h1>{person.name} {person.surname}</h1>
      <p>{person.bio}</p>
      <ul class="socials">
        <li><a href={person.github_handle}>Github</a></li>
        <li><a href={person.website}>Website</a></li>
      </ul>
      <h2>Mijn projecten</h2>
      <ul class="projects">
        <li class="project-card">
          <h3>Project 1</h3>
          <h4>Investables</h4>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores
            natus eveniet sapiente ipsam quidem vel! Eius voluptas reiciendis
            illum asperiores .
          </p>
          <a> Klikken </a>
        </li>
        <li class="project-card">
          <h3>Project 1</h3>
          <h4>Investables</h4>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores
            natus eveniet sapiente ipsam quidem vel! Eius voluptas reiciendis
            illum asperiores .
          </p>
          <a> Klikken </a>
        </li>
        <li class="project-card">
          <h3>Project 1</h3>
          <h4>Investables</h4>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores
            natus eveniet sapiente ipsam quidem vel! Eius voluptas reiciendis
            illum asperiores .
          </p>
          <a> Klikken </a>
        </li>
      </ul>
      <h2>My socials</h2>
    {:else}
      <!-- Als person data aan het laden is, laat dit zien -->
      <h1>Loading Data...</h1>
    {/if}
  </section>
</div>

<style>
  .wrapper {
    background-color: black;
    padding: 2rem;
    & .main-section {
      overflow: hidden;
      height: 100%;
      max-width: 800px;
      margin: 0 auto;
      & img {
        object-fit: cover;
        object-position: top;
      }
      & h1 {
        color: antiquewhite;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 3.5em;
        padding-top: 1.5rem;
        padding-bottom: 1.5rem;
        border-bottom: 4px dotted antiquewhite;
        margin: 0.25rem 0rem;
      }
      & h2 {
        color: antiquewhite;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 2.8em;
        padding-top: 1.5rem;
        padding-bottom: 1.5rem;
        border-top: 4px dotted orangered;
        border-bottom: 4px dotted antiquewhite;
        margin: 0.25rem 0rem;
      }
      & p {
        color: antiquewhite;
        font-family: Arial, Helvetica, sans-serif;
        margin-bottom: 1.5rem;
        border-left: 4px dotted antiquewhite;
        padding-left: 1rem;
        font-size: 1.5em;
      }
      & ul {
        list-style-type: none;
        padding-inline-start: 1rem;
        padding-bottom: 0.5rem;
        border-left: 4px dotted orangered;
      }
      & .socials {
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
        & a {
          font-size: 1.5em;
          font-family: Arial, Helvetica, sans-serif;
          color: rgb(255, 69, 0);
          text-decoration: underline;
          text-underline-offset: 4px;
          transition: ease-out 0.3s;
          &:hover,
          &:focus {
            border-radius: 4px;
            background-color: antiquewhite;
            padding: 10px 50px;
            transition: ease-in 0.2s;
            text-underline-offset: 8px;
            color: rgb(232, 63, 2);
          }
        }
      }
      & .projects {
        max-width: 100%;
        display: flex;
        gap: 2em;
        overflow-x: auto;
        scroll-snap-type: proximity;
        scroll-snap-align: center;
        padding-left: 2.5em;
        & h3 {
          color: antiquewhite;
          font-family: Arial, Helvetica, sans-serif;
          font-size: 2em;
          padding-top: 1.5rem;
          padding-bottom: 1.5rem;
          margin: 0.25rem 0rem;
        }
        & h4 {
          color: orangered;
          font-family: Arial, Helvetica, sans-serif;
          font-size: 1.3em;
          margin: 0px;
        }
        & .project-card {
          min-width: 450px; /* Ensure each project card has a minimum width */
          display: flex;
          flex-direction: column;
          transition: ease-out 0.2s;
          padding: 0em 2em;
          & a {
            display: none;
          }
          &:hover {
            cursor: pointer;
            transition: ease-in 0.2s;
            background-color: antiquewhite;
            padding-bottom: 2em;
            & h3 {
              color: orangered;
            }
            & p {
              color: black;
              border-left: 4px dotted black;
            }
            & a {
              display: block;
              font-size: 1.5em;
              font-family: Arial, Helvetica, sans-serif;
              color: rgb(255, 69, 0);
              text-decoration: underline;
              text-underline-offset: 4px;
              transition: ease-out 0.3s;
              &:hover,
              &:focus {
                border-radius: 4px;
                background-color: antiquewhite;
                transition: ease-in 0.2s;
                text-underline-offset: 8px;
                color: rgb(232, 63, 2);
              }
            }
          }
        }
      }
    }
  }
</style>
