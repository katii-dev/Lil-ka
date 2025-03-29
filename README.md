# Lil-ka
<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Obter Localização</title>
</head>
<body>
    <h2>Clique no botão para obter sua localização:</h2>
    <button onclick="getLocation()">Obter Localização</button>
    <p id="location"></p>

    <script>
        function getLocation() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(showPosition, showError);
            } else {
                document.getElementById("location").innerHTML = "Geolocalização não suportada pelo seu navegador.";
            }
        }

        function showPosition(position) {
            let latitude = position.coords.latitude;
            let longitude = position.coords.longitude;
            document.getElementById("location").innerHTML = `Latitude: ${latitude} <br> Longitude: ${longitude}`;
        }

        function showError(error) {
            switch(error.code) {
                case error.PERMISSION_DENIED:
                    alert("Você negou a solicitação de localização.");
                    break;
                case error.POSITION_UNAVAILABLE:
                    alert("Informações de localização indisponíveis.");
                    break;
                case error.TIMEOUT:
                    alert("A solicitação expirou.");
                    break;
                case error.UNKNOWN_ERROR:
                    alert("Ocorreu um erro desconhecido.");
                    break;
            }
        }
    </script>
</body>
</html>
