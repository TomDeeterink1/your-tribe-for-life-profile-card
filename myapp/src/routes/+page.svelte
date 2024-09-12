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
        <img src="{person.avatar}" width="200px" height="240px">
        <h1>{person.name} {person.surname}</h1> 
        <p>{person.bio}</p>
        <ul class="socials">
            <li><a href="{person.github_handle}">Github</a></li>
            <li><a href="{person.website}">Website</a></li>
        </ul>
        {:else}
            <!-- Als person data aan het laden is, laat dit zien -->
        <h1>Loading Data...</h1>
        {/if}
    
    </section>
</div>

<style>
   .wrapper{
     background-color: black;
     padding: 2rem;
     & .main-section{
        height: 100vh;
        max-width: 800px;
        margin: 0 auto;
        & img{
            object-fit: cover;
            object-position: top;
        }
        & h1{
            color: antiquewhite;
            font-family: Arial, Helvetica, sans-serif;
            font-size: 3.5em;
            padding-top: 1.5rem;
            padding-bottom: 1.5rem ;
            border-bottom: 2px solid antiquewhite;
            margin: 0.25rem 0rem;
        }
        & p{
            color: antiquewhite;
            font-family: Arial, Helvetica, sans-serif;
            margin-bottom: 1.5rem;
            border-left: 2px solid antiquewhite;
            padding-left: 1rem;
            font-size: 1.5em;
        }
        & ul{
            list-style-type: none;
            padding-inline-start: 1rem;
            padding-bottom: 0.5rem;
            border-left: 2px solid orangered;
        }
        & .socials{
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
                & a{
                font-size: 1.5em;
                font-family: Arial, Helvetica, sans-serif;
                color: orangered;
                text-decoration: underline;
                text-underline-offset: 4px;
                transition: ease-out 0.3s;
                
                    &:hover , &:focus{
                        border-radius: 4px;
                        background-color: antiquewhite;
                        padding: 10px 50px;
                        transition: ease-in 0.2s;
                        text-underline-offset: 8px;
                        color: rgb(232, 63, 2);
                    }
                }
        }
     }
   }
   
</style>