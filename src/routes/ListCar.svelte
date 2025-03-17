<script>
  import ZoomOnCar from "./ZoomOnCar.svelte";

  let { car, addCarToLibrary, moreInfo, zoomExit, upList, downList } = $props();
    let carlength = $state(car.length - 1)

</script>

<ul>
  {#each car as car, index}
    <li>
      <div class="carPicture">
        <img src={car.image} alt={car.name}  />
      </div>
      <div class="carDescription">
        <h2 class="nameCar">{car.name}</h2>
        <h3 class="typeOfTheCar">{car.categorie}</h3>
      </div>
      <div class="buttonAddCarToLibrary">
        {#if !car.like}
          <div class="centralized">
            <button
              class="buttonAddLibrary"
              onclick={() => addCarToLibrary(index)}
            >
              +
            </button>
          </div>
        {:else}
          <div class="centralized">
            <button class="buttonTakeOFLibrary"> ✓ </button>
          </div>
        {/if}
        <div class="buttonUpAndDown">
          <div class="up">
            {#if index != 0}
              <button class="buttonUp" onClick={() => upList(index)}
                >&uarr;</button
              >
            {/if}
          </div>
          <div class="down">
            {#if index != carlength}
              <button class="buttonDown" onClick={() => downList(index)}
                >&darr;</button
              >
            {/if}
          </div>
        </div>
      </div>
    </li>
    <hr />
    {#if car.zoom}
      <ZoomOnCar {car} {index}/>
    {/if}
  {/each}
</ul>

<style>
  @import "./reset.css";
  @import "./style.css";
</style>
