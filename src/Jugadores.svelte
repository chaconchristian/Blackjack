<script>
    export let suma;
    export let mesa;

    
</script>

<body class="Cuerpo">
    <div class="container">
        <div id="Jugador1" class="col">
            <h3>
                Jugador<br /> Valor: {suma}
            </h3>
            <br />
            {#each mesa as naipe}
                <img
                    class="carta"
                    src="./assets/cartas/{naipe}.png"
                    alt="xxx"
                />
            {/each}
        </div>
    </div>
</body>

<style>
    .carta {
        position: relative;
        height: 180px;
        left: 100px;
        margin-left: -75px;
    }
    .Cuerpo {
        height: 100vh;
        background-color: darkgreen;
    }

    #Jugador1 {
        color: white;
    }
</style>
