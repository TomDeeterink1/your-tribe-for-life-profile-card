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
    <section class="card">
        {#if person} 
        <!-- Als person data geladen is, laat dit zien -->
        <h1>{person.name} {person.surname}</h1> 
    
        <p>{person.bio}</p>
        <ul>
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
    body{
        margin: none;
    }
    .wrapper{
        width: 100%;
        height: 100vh;
        display: flex;
        align-items: center;
    }
    .card{
        margin: 0 auto;
        margin-bottom: 60px;
        padding: 2.2em;
        width: 300px;
        border: 8px groove white;
        border-radius: 4px;
        border-style: double;
        background:  url(boston-public-library-YoXxWEPOawY-unsplash.jpeg) ;
        background-size: cover;
        transition: ease-out 0.7s;
        background-position: center;
        &:hover{
            cursor: pointer;
            transform: scale(110%);
            transition: ease-in 0.6s; 
            background-position: bottom;
            background-size: 400%;
        }
        & h1 , p , a{
            font-family: 'Times New Roman', Times, serif;
            color: rgb(6, 6, 6);
            font-weight: 500;
        }
        & ul{
            list-style-type: none;
            padding-inline-start: 0px;
            display: flex;
            gap: 2.2em;
        }
        & a{
            text-decoration: underline;
            text-underline-offset: 0.25em;
            font-weight: 500;
            transition: ease-out 0.3s;
            &:hover{
                text-underline-offset: 0.50em;
                cursor: pointer;
                transition: ease-in 0.3s;

            }
        }
    }
</style>