<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Somme de temps</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 700px;
      margin: 50px auto;
      padding: 20px;
      background: #f5f5f5;
    }

    h1 {
      text-align: center;
      color: #c62828;
      font-size: 28px;
    }

    .bloc {
      background: white;
      padding: 20px;
      margin: 15px 0;
      border-radius: 5px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }

    .bloc h3 {
      margin: 0 0 15px 0;
      color: #333;
    }

    .ligne {
      display: flex;
      align-items: center;
      margin: 10px 0;
      gap: 15px;
    }

    label {
      font-weight: bold;
      min-width: 100px;
    }

    input {
      padding: 10px;
      border: 2px solid #ccc;
      border-radius: 4px;
      font-size: 16px;
      width: 120px;
    }

    .resultat {
      background: #e3f2fd;
      padding: 20px;
      margin: 20px 0;
      border-radius: 5px;
      border: 3px solid #1976d2;
    }

    .resultat h3 {
      margin: 0 0 15px 0;
      color: #1565c0;
    }

    .resultat input {
      background: #fff;
      border: 2px solid #1976d2;
      font-weight: bold;
    }

    .boutons {
      display: flex;
      gap: 15px;
      justify-content: center;
      margin-top: 25px;
    }

    button {
      padding: 15px 40px;
      font-size: 18px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
      transition: 0.3s;
    }

    .btn-somme {
      background: #4CAF50;
      color: white;
    }

    .btn-somme:hover {
      background: #388e3c;
    }

    .btn-effacer {
      background: #f44336;
      color: white;
    }

    .btn-effacer:hover {
      background: #c62828;
    }
  </style>
</head>
<body>

  <h1>TP – JavaScript : Exercice 4</h1>

  <div class="bloc">
    <h3>Enter le premier temps :</h3>
    <div class="ligne">
      <label>Heure(s)</label>
      <input type="number" id="h1" value="0" min="0">
      <label>Minute(s)</label>
      <input type="number" id="m1" value="0" min="0">
      <label>Seconde(s)</label>
      <input type="number" id="s1" value="0" min="0">
    </div>
  </div>

  <div class="bloc">
    <h3>Enter le Deuxième temps :</h3>
    <div class="ligne">
      <label>Heure(s)</label>
      <input type="number" id="h2" value="0" min="0">
      <label>Minute(s)</label>
      <input type="number" id="m2" value="0" min="0">
      <label>Seconde(s)</label>
      <input type="number" id="s2" value="0" min="0">
    </div>
  </div>


  <div class="bloc">
    <h3>Enter le troisième temps :</h3>
    <div class="ligne">
      <label>Heure(s)</label>
      <input type="number" id="h3" value="0" min="0">
      <label>Minute(s)</label>
      <input type="number" id="m3" value="0" min="0">
      <label>Seconde(s)</label>
      <input type="number" id="s3" value="0" min="0">
    </div>
  </div>


  <div class="resultat">
    <h3>Total des trois temps :</h3>
    <div class="ligne">
      <label>Jour(s)</label>
      <input type="text" id="jours" readonly>
      <label>Heure(s)</label>
      <input type="text" id="heures" readonly>
      <label>Minute(s)</label>
      <input type="text" id="minutes" readonly>
      <label>Seconde(s)</label>
      <input type="text" id="secondes" readonly>
    </div>
  </div>


  <div class="boutons">
    <button class="btn-somme" onclick="calculerSomme()">Somme</button>
    <button class="btn-effacer" onclick="effacer()">Effacer</button>
  </div>

  <script>
    function calculerSomme() {
    
      let h1 = parseInt(document.getElementById('h1').value) || 0;
      let m1 = parseInt(document.getElementById('m1').value) || 0;
      let s1 = parseInt(document.getElementById('s1').value) || 0;

      let h2 = parseInt(document.getElementById('h2').value) || 0;
      let m2 = parseInt(document.getElementById('m2').value) || 0;
      let s2 = parseInt(document.getElementById('s2').value) || 0;

      let h3 = parseInt(document.getElementById('h3').value) || 0;
      let m3 = parseInt(document.getElementById('m3').value) || 0;
      let s3 = parseInt(document.getElementById('s3').value) || 0;

    
      let totalSecondes = (h1 * 3600 + m1 * 60 + s1) +
                          (h2 * 3600 + m2 * 60 + s2) +
                          (h3 * 3600 + m3 * 60 + s3);

   
      let jours = Math.floor(totalSecondes / 86400);
      totalSecondes = totalSecondes % 86400;

      let heures = Math.floor(totalSecondes / 3600);
      totalSecondes = totalSecondes % 3600;

      let minutes = Math.floor(totalSecondes / 60);
      let secondes = totalSecondes % 60;

      // Afficher les résultats
      document.getElementById('jours').value = jours;
      document.getElementById('heures').value = heures;
      document.getElementById('minutes').value = minutes;
      document.getElementById('secondes').value = secondes;
    }

    function effacer() {
      // Effacer les entrées
      document.getElementById('h1').value = 0;
      document.getElementById('m1').value = 0;
      document.getElementById('s1').value = 0;

      document.getElementById('h2').value = 0;
      document.getElementById('m2').value = 0;
      document.getElementById('s2').value = 0;

      document.getElementById('h3').value = 0;
      document.getElementById('m3').value = 0;
      document.getElementById('s3').value = 0;

      // Effacer les résultats
      document.getElementById('jours').value = '';
      document.getElementById('heures').value = '';
      document.getElementById('minutes').value = '';
      document.getElementById('secondes').value = '';
    }
  </script>

</body>
</html>
