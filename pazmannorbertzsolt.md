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