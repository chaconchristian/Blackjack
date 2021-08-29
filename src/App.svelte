<script>
	import Jugadores from "./Jugadores.svelte";
	import Computadora from "./Computadora.svelte";
	import { shuffle } from "./underscore-esm-min";

	const numeros = [2, 3, 4, 5, 6, 7, 8, 9, 10];
	const tipos = ["C", "D", "S", "H"];
	const especiales = ["A", "J", "Q", "K"];

	let deck = [];
	let mesa=[];

// Esta funcion permite crear la baraja
const construirDeck = () => {
	for (const num of numeros) {
		for (const tipo of tipos) {
			deck = [...deck, num + tipo];
		}
	}
	for (const esp of especiales) {
		for (const tipo of tipos) {
			deck = [...deck, esp + tipo];
		}
	}
	deck = shuffle(deck);
	// console.log({ deck });
};
construirDeck();

// esta funcion permite tomar carta
let carta ="" ;

	const pedirCarta = () => {
		carta = deck.pop();
		mesa=[...mesa,carta]
		deck = deck;
		
		return carta;
	
	};
	pedirCarta();

	// Esta función determina el valor de la carta sacada

	const valorcarta = (carta) => {
		let valor = carta.substring(0, carta.length - 1)
		
		return isNaN(valor) ? (valor === "A" ? 11 : 10) : valor * 1
		}	
	valorcarta(carta);


	

</script>

<main>
	<header class="Cabecera">
		<h1>Blackjack</h1>
		<br />
		<div class="container">
			<div class="row">
				<div class="col">
					<button class="btn btn-success"> Nuevo juego </button>
				</div>
				<div class="col">
					<button class="btn btn-primary" on:click={pedirCarta}>Pedir Carta
					</button>
				</div>
				<div class="col">
					<button class="btn btn-danger"> Salir </button>
				</div>
			</div>
		</div>
	</header>
	<body>
		<Jugadores  {mesa} />
	</body>
	<footer class="Piepagina">
		<div class="row">
			<div class="col">
				<div class="container">Derechos reservados</div>
			</div>
		</div>
	</footer>
</main>

<style>
	.Cabecera {
		text-align: center;
		background-color: black;
		color: white;
	}

	.Piepagina {
		background-color: chocolate;
	}
</style>
