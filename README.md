<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Trier un tableau</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 600px;
      margin: 50px auto;
      padding: 20px;
      background: #f0f0f0;
    }

    h1 {
      text-align: center;
      color: #333;
    }

    .form-group {
      margin: 20px 0;
    }

    label {
      display: block;
      margin-bottom: 8px;
      font-weight: bold;
    }

    input {
      width: 100%;
      padding: 12px;
      font-size: 16px;
      border: 2px solid #ddd;
      border-radius: 5px;
      box-sizing: border-box;
    }

    button {
      width: 100%;
      padding: 12px;
      font-size: 18px;
      background: #4CAF50;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 10px;
    }

    button:hover {
      background: #45a049;
    }

    .resultat {
      margin-top: 20px;
      padding: 20px;
      background: white;
      border-radius: 5px;
      border: 2px solid #4CAF50;
    }

    .resultat h3 {
      margin-top: 0;
      color: #4CAF50;
    }

    .liste {
      font-size: 18px;
      font-weight: bold;
      color: #333;
      margin: 10px 0;
    }

    .exemple {
      background: #e3f2fd;
      padding: 15px;
      border-radius: 5px;
      margin-top: 20px;
    }

    .exemple h3 {
      margin-top: 0;
      color: #1976d2;
    }
  </style>
</head>
<body>

  <h1>🔢 Trier un tableau de nombres</h1>

  <div class="form-group">
    <label for="nombres">Entrez des nombres séparés par des virgules :</label>
    <input type="text" id="nombres" placeholder="5, 2, 8, 1, 9, 3">
  </div>

  <button onclick="trierEtAfficher()">Trier</button>

  <div class="resultat" id="resultat" style="display: none;">
    <h3>📊 Résultat :</h3>
    <div class="liste">Liste originale : <span id="original"></span></div>
    <div class="liste">Liste triée : <span id="triee"></span></div>
  </div>

  <div class="exemple">
    <h3>💡 Exemples :</h3>
    <p><strong>Entrée :</strong> 5, 2, 8, 1, 9</p>
    <p><strong>Sortie :</strong> 1, 2, 5, 8, 9</p>
    <br>
    <p><strong>Entrée :</strong> 42, 15, 3, 100, 7</p>
    <p><strong>Sortie :</strong> 3, 7, 15, 42, 100</p>
  </div>

  <script>
    // Fonction pour trier un tableau de nombres
    function trier(liste) {
      // Créer une copie pour ne pas modifier l'original
      let copie = [...liste];
      
      // Trier du plus petit au plus grand
      copie.sort(function(a, b) {
        return a - b;
      });
      
      return copie;
    }

    // Fonction pour afficher le résultat
    function trierEtAfficher() {
      // Récupérer l'input
      let texte = document.getElementById('nombres').value;
      
      // Vérifier si vide
      if (texte === '') {
        alert('Veuillez entrer des nombres');
        return;
      }
      
    
      let tableau = texte.split(',').map(function(n) {
        return parseInt(n.trim());
      });
      
      for (let i = 0; i < tableau.length; i++) {
        if (isNaN(tableau[i])) {
          alert('Erreur : Entrez uniquement des nombres séparés par des virgules');
          return;
        }
      }
 
      let tableauTrie = trier(tableau);
      
  
      document.getElementById('original').textContent = tableau.join(', ');
      document.getElementById('triee').textContent = tableauTrie.join(', ');
      document.getElementById('resultat').style.display = 'block';
    }

  
    document.getElementById('nombres').addEventListener('keypress', function(e) {
      if (e.key === 'Enter') {
        trierEtAfficher();
      }
    });
  </script>

</body>
</html>
