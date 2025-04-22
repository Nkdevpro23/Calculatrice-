
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculatrice</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="calculatrice">
        <input type="text" id="ecran" disabled>
        <div class="boutons">
            <button id="bouton7">7</button>
            <button id="bouton8">8</button>
            <button id="bouton9">9</button>
            <button id="boutonDiv">/</button>
            <button id="bouton4">4</button>
            <button id="bouton5">5</button>
            <button id="bouton6">6</button>
            <button id="boutonMult">*</button>
            <button id="bouton1">1</button>
            <button id="bouton2">2</button>
            <button id="bouton3">3</button>
            <button id="boutonSoustr">-</button>
            <button id="bouton0">0</button>
            <button id="boutonVirgule">.</button>
            <button id="boutonEgal">=</button>
            <button id="boutonAdd">+</button>
            <button id="boutonC">C</button>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
<style>
.calculatrice {
    width: 200px;
    margin: 50px auto;
    padding: 20px;
    background-color:azure;
    border: 1px solid #ccc;
    border-radius: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

#ecran {
    width: 90%;
    height: 40px;
    margin-bottom: 20px;
    padding: 10px;
    font-size: 24px;
    font-weight: bold;
    text-align: right;
    border: none;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.boutons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 10px;
}

button {
    width: 100%;
    height: 40px;
    font-size: 18px;
    font-weight: bold;
    border: none;
    border-radius: 10px;
    background-color: #4CAF50;
    color: #fff;
    cursor: pointer;
}

button:hover {
    background-color: #3e8e41;
}
</style>
<script>
let ecran = document.getElementById("ecran");
let historique = "";

document.querySelectorAll("button").forEach(bouton => {
    bouton.addEventListener("click", () => {
        let valeur = bouton.textContent;

        if (valeur === "=") {
            try {
                let resultat = eval(historique);
                ecran.value = resultat;
                historique = resultat.toString();
            } catch (error) {
                ecran.value = "Erreur";
                historique = "";
            }
        } else if (valeur === "C") {
            ecran.value = "";
            historique = "";
        } else {
            historique += valeur;
            ecran.value = historique;
        }
    });
});
function calculer() {
  let resultat;

  switch (operateur) {
    case '+':
      resultat = parseFloat(valeurPrecedente) + parseFloat(valeurActuelle);
      break;
    case '-':
      resultat = parseFloat(valeurPrecedente) - parseFloat(valeurActuelle);
      break;
    case '*':
      resultat = parseFloat(valeurPrecedente) * parseFloat(valeurActuelle);
      break;
    case '/':
      resultat = parseFloat(valeurPrecedente) / parseFloat(valeurActuelle);
      break;
    default:
      resultat = valeurActuelle;
  }

  affichage.value = resultat.toString();
}
</script>