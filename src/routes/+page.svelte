<style>
    @import './reset.css';
    @import './style.css';
</style>

<script>
    import ListCar from './ListCar.svelte';
    import Library from './Library.svelte';

    let car = $state([]);
    let library = $state([])

    import json from '../lib/voiture.json'
    car = json;

    const ferrari = function () {
        car.push({
                  id: "f8 tributo",
                  name: "ferrari f8 tributo",
                  categorie: "hypercar",
                  image:
                    "https://www.circuit-mirecourt.fr/wp-content/uploads/2023/10/rc-events_0002_dsc04106-scaled.jpg",
                  like: false,
                  zoom: false,
                          "desc": "La Ferrari F8 Tributo embarque un V8 biturbo 3.9L de 720 ch, 0-100 km/h en 2,9 s, propulsion affûtée, aérodynamisme optimisé, intérieur luxueux et technologies dérivées de la F1 pour une performance exaltante."
                })
    }

    const C2 = function () {
        car.push(
            {
                  id: "c2",
                  name: "citroën C2",
                  categorie: "Bête férroce",
                  image:
                    "https://img.leboncoin.fr/api/v1/lbcpb1/images/70/3a/e9/703ae9184223cb606d71c9246a14680f20880a8c.jpg?rule=ad-large",
                  like: false,
                  zoom: false,
                  desc: "La Citroën C2 est une petite citadine au design compact et dynamique, disponible avec des moteurs essence et diesel (60 à 125 ch pour la VTS), une boîte manuelle ou Sensodrive, et une bonne agilité urbaine."
                }
        )
    }

    const porsche = function () {
        car.push(
            {
                  id: "911 gt3rs",
                  name: "porsche 911 gt3rs",
                  categorie: "hypercar",
                  image:
                    "https://pictures.porsche.com/rtt/iris?COSY-EU-100-1711coMvsi60AAt5FwcmBEgA4qP8iBUDxPE3Cb9pNXkBuNYdMGF4tl3U0%25z8rMHIspbWvanYb%255y%25oq%25vSTmjMXD4qAZeoNBPUSfUx4RmHlCgI7Zl2dioCxkF%25vUqCNwuWXsOw3meV6iTCj%25zhRc2GRdqAZ%25oD21P%25S1BAXmenugTfeIJpV7nDhQk",
                  like: false,
                  zoom: false,
                  desc: "La Porsche 911 GT3 RS est une sportive radicale avec un flat-6 atmosphérique 4.0L de 525 ch, 0-100 km/h en 3,2 s, aérodynamisme extrême, châssis affûté, propulsion, boîte PDK et un comportement taillé pour le circuit."
                }
        )
    }

    const addCarToLibrary = function(index) {
        library.push(car[index])
        car[index].like = true
    }

    const moreInfo = function(index) {
        car[index].zoom = true;
    }


    const upList = function (index) {
        if (index > 0) {
            let newArray = [...car.slice(0, index), ...car.slice(index + 1)]
            newArray.splice(index - 1, 0, car[index]);
            car = newArray;
        } else {
            return
        }
    }

    const downList = function (index) {
        if (index < car.length - 1) {
            let newArray = [...car.slice(0, index), ...car.slice(index + 1)]
            newArray.splice(index - 1, 0, car[index]);
            car = newArray;
        } else {
            return
        }
    }
</script>

<div class="newList">
    <div>
        <div class="divButtonAddCar">
            <button class="buttonAddCar" onclick={() => ferrari()}>
                add a ferrari
            </button>
            <button class="buttonAddCar" onclick={C2}>
                add an amazing car
            </button>
            <button class="buttonAddCar" onclick={porsche}>
                add a porsche
            </button>
        </div>
        <ListCar 
            car = {car}
            addCarToLibrary={(e) => addCarToLibrary(e)}
            moreInfo={(e) => moreInfo(e)}
            zoomExit={(e) => zoomExit(e)}
            upList={(e) => upList(e)}
            downList={(e) => downList(e)}
        />
        <Library library = {library}/>
    </div>
</div>