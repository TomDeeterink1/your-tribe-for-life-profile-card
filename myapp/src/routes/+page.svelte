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
<section class="next">
    Your eyes can deceive you; don’t trust them
</section>


<style>
    .card{
        margin: 0 auto;
        margin-top: 10%;
        padding: 2em;
        width: 300px;
        border: 8px groove white;
        border-radius: 4px;
        border-style: double;
        background:  url(boston-public-library-YoXxWEPOawY-unsplash.jpeg) ;
        background-size: cover;
        transition: ease-out 0.3s;
        &:hover{
            cursor: pointer;
            margin-bottom: -50px;
            transform: scale(105%);
            transition: ease-in 0.3s; 
        }
        &:target{
            transform: scale(1005%);
        }
        & h1 , p , a{
            font-family: 'Times New Roman', Times, serif;
            color: white;
        }
        & ul{
            list-style-type: none;
            padding-inline-start: 0px;
            display: flex;
            gap: 1em;
            & li{

            }
        }
        & a{
            text-decoration: none;
            font-weight: 600;
            &:hover{
                cursor: pointer;

            }
        }
    }
    .next{
        margin: 0 auto;
        width: max-content;
        padding: 2em;
        & a{
            text-decoration: none;
            font-weight: 600;
            &:hover{
                cursor: pointer;

            }
        }
    }
</style>