<style>
    @import './reset.css';
    @import './style.css';
</style>

<script>
  let { car, index } = $props();

  function zoomExit () {
    car[index].zoom = false;
    console.log("ok");
  };
</script>

<div class="background">
  <div class="zoom">
    <img src={car.image} alt={car.name} />
    <h2 class="zoomCarName">{car.name}</h2>
    <h3 class="zoomTypeOfCar">{car.categorie}</h3>
    <p class="zoomCarDesc">{car.desc}</p>
    <button class="zoomExit" onClick={() => zoomExit()}>X</button>
  </div>
</div>
