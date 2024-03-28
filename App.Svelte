https://github.com/Camilacauzzo/tpVD.git

<!-- Script JS -->
<script>
    let selectedImage = null
    let magnitudes = [25, 50, 75, 100]; // array de magnitudes
    let imagenes = ['./images/dom.png', './images/menta.png', './images/copo.png', './images/flor.png']; // array de imágenes

    function mostrarImagen (i) {
        selectedImage = i
        console.log("index de img seleccionada", selectedImage)
    }

</script>

<!-- Estructura contenido HTML -->
<div class="container">
    <h1 class="titulo">Representación de distintas magnitudes en el consumo de agua de una persona</h1>
        <div class="buttons">
            {#each ["", "", "", ""] as button, i}
                <button on:click={() => mostrarImagen(i)}>
                    <img src={imagenes[i]} alt={button} style="width: 50px;" /> <!-- Assign image to button as an icon with a width of 50px -->
                    {button}
                </button>
            {/each}
            
        </div>

       
</div>    

<div class="col-container">
    {#each magnitudes as m, i}
    <div class="col-wrap" class:show-mask={selectedImage === i}>
        <div class = 'column' style='height: {m*2}px' ></div>
        <img class = 'mask' src="./images/tipo.png" alt="" >
    </div>

{/each}
</div>


<!-- Estilos CSS -->
<style>
    .container{
        display: flex;
        flex-direction: column;
    
    }
    .titulo{
        font-family: 'Times New Roman', Times, serif;
        font-weight: bold;
        text-decoration: underline;
        text-align: center;
    }
    .buttons{
        display: flex;
        justify-content: center;
    }
    .col-container{
        
        display: flex;
        align-items: flex-end;
        justify-content:center;
    }
    .column{
        background-color: blue;
        /*background-image: './images/agua.jpg';*/
        width: 100px;
        /* display: none; */
        
    }
    .mask{
        width: 100px;
        height:200px; /*sale columna por abajo xq el svg tiene parte por abajo de borde de figura*/
        position: absolute;
        bottom: 0;
        z-index: 1;
    }

    .show-mask {
        display: block !important;
    }
    .col-wrap{
        position: relative;
        width: 100px;
        margin: 10px;
        display: none;
    }


</style>
