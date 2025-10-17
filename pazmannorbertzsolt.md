📄 dokumentacio.md
🌐 Weboldal témája

A projekt egy "Napi egészségkövető alkalmazás", amely segít a felhasználónak nyomon követni a napi vízfogyasztását, megtett lépéseit, valamint az alvásidejét. A felhasználó megadhatja napi adatait, és az oldal összegzi, elemzi és visszajelzést ad ezek alapján.

🛠️ Használt technológiák

HTML – A weboldal struktúrájához.

CSS – A weboldal megjelenésének kialakításához.

JavaScript – A logikai működéshez, interakciókhoz, számításokhoz.

📄 Weboldal felépítése

index.html – Főoldal, bemutatja az alkalmazást és lehetőség van az adatok bevitelére (víz, lépésszám, alvásidő).

statisztika.html – Megjeleníti a napi adatokból számolt statisztikákat (összes vízfogyasztás, alvás átlag, stb.).

tippek.html – Egészségügyi tippeket jelenít meg, ha az adatok nem felelnek meg az ajánlott értékeknek.

🧠 JavaScript függvények

osszviz(vizek)

📌 Funkció: Összegzi a tömbben lévő vízmennyiségeket (liter).

🧮 Programozási tétel: Összegzés.

📥 Paraméter: vizek – egy tömb a nap folyamán bevitt vizek mennyiségével.

🔁 Használ ciklust.

lepesElemzes(lepes)

📌 Funkció: Eldönti, hogy a megtett lépésszám elegendő volt-e (minimum 8000 lépés).

🧠 Elágazás, logikai művelet.

📥 Paraméter: lepes – a napi lépésszám.

alvasAtlag(orasTomb)

📌 Funkció: Kiszámítja az alvásórák átlagát egy héten.

🔁 Ciklussal dolgozik, visszatér az átlaggal.

tippGenerator(viz, lepes, alvas)

📌 Funkció: Visszaad egészségügyi tippeket, ha valamelyik érték túl alacsony.

🧠 Több elágazás, logikai művelet, tömb használata.




<!DOCTYPE html>
<html lang="hu">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Napi Egészségkövető</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 2rem;
      max-width: 800px;
      margin: auto;
      background-color: #f5f5f5;
    }

    h1, h2 {
      color: #2c3e50;
    }

    label {
      display: block;
      margin-top: 1rem;
      font-weight: bold;
    }

    input {
      padding: 0.5rem;
      width: 100%;
      margin-top: 0.3rem;
      box-sizing: border-box;
    }

    button {
      margin-top: 1.5rem;
      padding: 0.7rem 1.5rem;
      background-color: #3498db;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 4px;
    }

    button:hover {
      background-color: #2980b9;
    }

    .eredmeny, .tippek {
      margin-top: 2rem;
      padding: 1rem;
      background-color: #ecf0f1;
      border-radius: 4px;
    }

    .tippek ul {
      padding-left: 1.2rem;
    }

    .tippek li {
      margin-bottom: 0.5rem;
    }
  </style>
</head>
<body>

  <h1>🌿 Napi Egészségkövető Alkalmazás</h1>
  <p>Add meg az adataidat a mai napról, és az alkalmazás kiértékeli, hogyan teljesítettél!</p>

  <form id="egeszsegForm">
    <label for="viz">Vízfogyasztás (liter):</label>
    <input type="number" id="viz" name="viz" step="0.1" required>

    <label for="lepes">Lépésszám:</label>
    <input type="number" id="lepes" name="lepes" required>

    <label for="alvas">Alvásidő (óra):</label>
    <input type="number" id="alvas" name="alvas" step="0.1" required>

    <button type="submit">Kiértékelés</button>
  </form>

  <div class="eredmeny" id="eredmeny" style="display:none;">
    <h2>📊 Eredmények</h2>
    <p><strong>Összes vízfogyasztás:</strong> <span id="vizOssz"></span> liter</p>
    <p><strong>Lépésszám elegendő:</strong> <span id="lepesEredmeny"></span></p>
    <p><strong>Alvásidő:</strong> <span id="alvasOra"></span> óra</p>
  </div>

  <div class="tippek" id="tippek" style="display:none;">
    <h2>💡 Egészségügyi tippek</h2>
    <ul id="tippekLista"></ul>
  </div>

  <script>
    // Függvény: Összegzi a vízfogyasztást
    function osszviz(vizek) {
      let osszeg = 0;
      for (let i = 0; i < vizek.length; i++) {
        osszeg += vizek[i];
      }
      return osszeg;
    }

    // Függvény: Eldönti, elegendő-e a lépésszám
    function lepesElemzes(lepes) {
      return lepes >= 8000;
    }

    // Függvény: Alvásátlag kiszámítása
    function alvasAtlag(orasTomb) {
      let osszeg = 0;
      for (let i = 0; i < orasTomb.length; i++) {
        osszeg += orasTomb[i];
      }
      return osszeg / orasTomb.length;
    }

    // Függvény: Egészségügyi tippek generálása
    function tippGenerator(viz, lepes, alvas) {
      let tippek = [];

      if (viz < 2) {
        tippek.push("💧 Igyál több vizet! Legalább 2 liter ajánlott naponta.");
      }

      if (lepes < 8000) {
        tippek.push("🚶‍♂️ Növeld a mozgást! Legalább 8000 lépés a napi cél.");
      }

      if (alvas < 7) {
        tippek.push("🛌 Törekedj 7-8 óra alvásra naponta a jobb regenerációért.");
      }

      return tippek;
    }

    // Eseményfigyelő a form beküldésére
    document.getElementById('egeszsegForm').addEventListener('submit', function(e) {
      e.preventDefault();

      // Bemeneti értékek beolvasása
      const viz = parseFloat(document.getElementById('viz').value);
      const lepes = parseInt(document.getElementById('lepes').value);
      const alvas = parseFloat(document.getElementById('alvas').value);

      // Kiértékelés és megjelenítés
      document.getElementById('vizOssz').textContent = osszviz([viz]).toFixed(1);
      document.getElementById('lepesEredmeny').textContent = lepesElemzes(lepes) ? "✅ Igen" : "❌ Nem";
      document.getElementById('alvasOra').textContent = alvas.toFixed(1);

      document.getElementById('eredmeny').style.display = "block";

      // Tippek megjelenítése
      const tippek = tippGenerator(viz, lepes, alvas);
      const tippekLista = document.getElementById('tippekLista');
      tippekLista.innerHTML = "";

      if (tippek.length > 0) {
        tippek.forEach(tipp => {
          const li = document.createElement('li');
          li.textContent = tipp;
          tippekLista.appendChild(li);
        });
        document.getElementById('tippek').style.display = "block";
      } else {
        document.getElementById('tippek').style.display = "none";
      }
    });
  </script>

</body>
</html>