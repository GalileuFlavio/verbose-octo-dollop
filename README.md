# verbose-octo-dollop
Crie um arquivo JavaScript chamado "seguranca.js" e inclua-o na página HTML. Aqui está o exemplo de código

// Acessa os elementos HTML necessários
const cameraOnButton = document.getElementById("camera-on");
const cameraOffButton = document.getElementById("camera-off");
const sensorList = document.getElementById("sensor-list");

// Define uma função que será acionada quando um sensor de movimento for acionado
function sensorAtivado(sensor) {
	// Cria uma requisição para acionar a câmera
	const request = new XMLHttpRequest();
	request.open("POST", "/camera");
	request.send();
	console.log(`Câmera acionada pelo sensor ${sensor}`);
}

// Adiciona um event listener para cada sensor de movimento
sensorList.querySelectorAll("li").forEach((sensor) => {
	sensor.addEventListener("click", () => {
		sensorAtivado(sensor.textContent);
	});
});

// Adiciona event listeners para os botões da câmera
cameraOnButton.addEventListener("click", () => {
	// Cria uma requisição para ligar a câmera
	const request = new XMLHttpRequest();
	request.open("POST", "/camera/on");
	request.send();
	console.log("Câmera ligada");
});

cameraOffButton.addEventListener("click", () => {
	// Cria uma requisição para desligar a câmera
	const request = new XMLHttpRequest();
	request.open("POST", "/camera/off");
	request.send();
	console.log("Câmera desligada");
});
