var flecha = document.getElementById("flecha");
	var NumRodate = ["727.5", "742.5", "757.5", "772.5", "787.5", "802.5", "817.5", "832.5", "847.5", "862.5", "877.5", "892.5", "907.5", "922.5", "937.5", "952.5", "967.5", "982.5", "997.5", "1012.5", "1027.5", "1042.5", "1057.5", "1072.5"];
	var Accion = [
		"Pie izquierdo al color que quieras",
		"Pie izquierdo a rojo",
		"Pie izquierdo a verde",
		"Pie izquierdo al aire",
		"Pie izquierdo a amarillo",
		"Pie izquierdo a azul",

		"Mano derecha al color que quieras",
		"Mano derecha a rojo",
		"Mano derecha a verde",
		"Mano derecha al aire",
		"Mano derecha a amarillo",
		"Mano derecha a azul",

		"Pie derecho al color que quieras",
		"Pie derecho a rojo",
		"Pie derecho a verde",
		"Pie derecho al aire",
		"Pie derecho a amarillo",
		"Pie derecho a azul",

		"Mano izquierda al color que quieras",
		"Mano izquierda a rojo",
		"Mano izquierda a verde",
		"Mano izquierda al aire",
		"Mano izquierda a amarillo",
		"Mano izquierda a azul"
	];


	function Lanzar() {
		//Genera un numero al azar
		var NumRandom=Math.floor((Math.random()*(23-0+1))+0);

		//Posicion actual
		var RodateInicial = parseInt(flecha.style.transform.replace("rotate(", "").replace("deg)", ""), 10);
		if(RodateInicial>0){RodateInicial=RodateInicial-720;}else{RodateInicial=0;}

		//Animar
		flecha.animate([
			{transform: "rotate("+RodateInicial.toString()+"deg)"},
			{transform: "rotate("+NumRodate[NumRandom]+"deg)"}],
			{duration: 1000, easing: "ease-out"});
		flecha.style.transform = "rotate("+NumRodate[NumRandom]+"deg)";

		//Ejecucion programada para cuando termine la aniamacion
		setTimeout(function(){
			//Mensaje de voz de la accion
			speechSynthesis.speak(new SpeechSynthesisUtterance(Accion[NumRandom]));
		},1150);
	}
	document.getElementById("tablero").onclick = function() {Lanzar()};