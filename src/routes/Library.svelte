<style>
    @import './reset.css';
    @import './style.css';
</style>

<script>
    let {library} = $props();
</script>

<h1 class="library">Votre bibliothèque :</h1>
<div class="listLibrary">
    {#each library as car, index}
        {#if car.zoom}
            <div>
                <div class="descCarInLibrary">
                    <img src={car.image} alt={car.name}>
                    <h4 class="libraryName">{car.name}</h4>
                </div>
            </div>
        {/if}
        <div class="descCarInLibrary">
            <img src={car.image} alt={car.name}>
            <h4 class="libraryName">{car.name}</h4>
        </div>
    {/each}
</div>