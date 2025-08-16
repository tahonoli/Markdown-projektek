Az alábbi végső, letisztult, teljes, szimulációs prompt LLM-barát módon van megírva, hogy egyszerre legyen:

*   **strukturált** (ne essen szét az LLM-ben),
    
*   **teljes** (benne van minden: ToC, meta-kérdések, ensemble, k-fold=10, szenzitivitás, kimenetek),
    
*   **copy–paste ready**.

## PART-01: Prompt

NHM Szimulációs Prompt
=======================

**Cél**  
Számítsd ki Magyarország és Lengyelország számára a Nemzeti Hatékonysági Mutatót (NHM), amelyet 0–100 közé kell leképezni.  
A modell kísérleti, nincs egységes NHM a szakirodalomban, de legyen transzparens, rekonstruálható és interpretálható.

* * *

**Elméleti keret: NHM × Theory of Change**  
Értékeld mindkét országot a következő 8 pillér alapján:

1.  **Erőforrás- és adottságbázis (INPUT)**
    
    *   Mutatók: felsőfokú végzettség, PISA-eredmények, bruttó állótőke-képzés, szélessáv-penetráció, energiaimport-függés.
        
2.  **Intézményi minőség & jogállamiság (INPUT)**
    
    *   Mutatók: WGI Government Effectiveness, Rule of Law, TI-CPI.
        
3.  **Átalakítási hatékonyság (PROCESS)**
    
    *   Mutatók: TFP, GDP/foglalkoztatott (PPP), ipari/szolgáltatási termelékenység.
        
4.  **Tudás- és innovációs kapacitás (PROCESS)**
    
    *   Mutatók: GERD %GDP, szabadalmak/fő, idézett tudományos publikációk, startup-intenzitás/fő.
        
5.  **Piaci integráció & nemzetközi súly (OUTPUT)**
    
    *   Mutatók: magas minőségű export aránya, FDI/fő, EU-forrás lehívás aránya.
        
6.  **Társadalmi kimenetek & jóléti minőség (OUTCOME)**
    
    *   Mutatók: várható élettartam egészségben, mediánjövedelem (PPP), lakhatási megfizethetőség.
        
7.  **Fenntarthatóság & kockázati korrekció (RISK)**
    
    *   Mutatók: államadósság/GDP, költségvetési hiány, nettó CO₂/fő trend, demográfiai függőségi ráta.
        
8.  **Rezíliencia & koordinációs képesség (ADAPT)**
    
    *   Mutatók: katasztrófa-reakció idők, krízisprogram végrehajtás, választási részvételi stabilitás.
        

Ha nincs adat, adj meg transzparens proxykat.

* * *

**Meta-kör (futtasd először, külön blokként):**

1.  Adj listát a 20 legfontosabb tényezőről, amit mindig figyelembe kell venni egy NHM-ben.
    
2.  Mely mutatók hiányoznak leggyakrabban a mainstream indexekből?
    
3.  Ha csak 5 dimenziót választhatnál, melyik adna kb. 80%-os magyarázóerőt?
    
4.  Mi az a 10 kevésbé nyilvánvaló tényező, amitől félremehet a KPI, ha kimarad?
    

* * *

**Számítási eljárás**

*   Normalizálás: minden mutató 0–100 közé, irányhelyesen.
    
*   Kombinálás: Ensemble (egyenlő súly + PCA(1) + rang-átlag, átlagolva).
    
*   Robusztusság: k-fold=10 validáció, minden foldban 20% metrika-dropout, fold-átlag és szórás riport.
    
*   Szenzitivitás:  
    (a) „Minden közepes, kivéve X pillér” → hatás a végső KPI-ra.  
    (b) Leave-one-pillar-out és leave-one-metric-out → Δ pont riport.
    
*   Hozzájárulás: Shapley-szerű varianciahozzájárulás pillérszinten.
    

* * *

**Kimenetek**

1.  Végső NHM (0–100), külön Magyarországra és Lengyelországra.
    
2.  Hozam–kockázat 2D ábra.
    
3.  Pillér-hozzájárulások és szenzitivitási riport.
    
4.  Vakfolt-lista.
    
5.  Letölthető CSV-k + dokumentált Python kód:
    
    *   adatok előkészítése,
        
    *   normalizálás,
        
    *   ensemble számítás,
        
    *   cross-validation,
        
    *   szenzitivitási ábrák.
        

A Python kód legyen jól kommentált: tartalmazza mind a felhasználói logikát (hogyan futtatható), mind az elvi logikát (mi miért van).

* * *

🔚 **Instrukció**  
Most hajtsd végre a teljes folyamatot a fenti sorrendben, és a végén mutasd meg a végső NHM-értékeket, az összes kért kimenetet és a dokumentációt.

## PART-02: Manuálisan összeállított gondolkodási dokumentáció / prompt-váz, a szimulációt támogatandó (csatolmányban befűzve)

Prompt-váz elemjegyzék

**1. Cél és keret**
Egyértelmű cél rögzítése: 0–100 közé leképezett Nemzeti Hatékonysági Mutató (NHM) kiszámítása.
Két összehasonlítási ország: Magyarország és Lengyelország.
Kontextus: nincs egységes NHM-mutató a szakirodalomban → kísérleti, de transzparens modell a cél.

**2. Elméleti háttér**
NHM × Theory of Change integráció → az általunk kidolgozott 8 pillér (input–átalakítás–output–fenntarthatóság).  
Rögzíteni, hogy ezek pillérszinten is értékelendők, nem csak aggregált KPI.  
ToC-leképezés: Inputok (1–2) → Folyamat/Átalakítás (3–4) → Output/Outcome (5–6) → Kockázati korrekció & Adaptáció (7–8)  
    **Erőforrás- és adottságbázis (INPUT)**  
    - Mit mér: humán, tőke, digitális/infrastruktúra, természeti/energia-adottság.  
    - Must-have: (i) képzett munkaerő: felsőfokú arány, PISA; (ii) tőkeállomány/fő vagy bruttó állótőke-képzés; (iii) szélessáv + logisztikai index; (iv) energiaimport-függés.  
    - Nice-to-have: egészségben eltöltött évek, ipari villamosenergia-ár.  
    **Intézményi minőség & jogállamiság (INPUT)**  
    Mit mér: kormányzati hatékonyság, közbeszerzés minősége, korrupció-kockázat.  
    Must-have: WGI Government Effectiveness, Rule of Law; TI-CPI.  
    Nice-to-have: bírósági átfutási idők, közbeszerzési verseny mutatók.  
    Átalakítási hatékonyság (PROCESS)  
    Mit mér: mennyire fordítja az ország az inputokat versenyképes hozzáadott értékké.  
    Must-have: TFP (total factor productivity), GDP/foglalkoztatott (PPP), ipari/ szolgáltatási termelékenység.  
    Nice-to-have: ellátási lánc-fordulat (value-added share a kivitelben), állami projektvégrehajtás csúszásráta.  
    Tudás- és innovációs kapacitás (PROCESS)  
    Mit mér: K+F input→output lánc, tudásáramlás.  
    Must-have: GERD %GDP; EPO/PCT szabadalmak/fő vagy tudományos cikkek normalizált idézettsége; startup-intenzitás/fő.  
    Nice-to-have: vállalati K+F részaránya; egyetem-ipar co-publications.  
    Piaci integráció & nemzetközi súly (OUTPUT)  
    Mit mér: globális beágyazottság, forráslehívás, szövetségi leverage.  
    Must-have: magas minőségű export aránya (tech- vagy komplexitási index); FDI-készlet/fő; EU-forrás lehívási arány vagy NATO-vállalás teljesítése.  
    Nice-to-have: hyperscaler/regionális DC jelenlét, logisztikai hub-mutatók.  
    Társadalmi kimenetek & jóléti minőség (OUTCOME)  
    Mit mér: az előállított érték „minősége” a lakosság szempontjából.  
    Must-have: várható élettartam egészségben; jövedelmi medián/PPP; lakhatási megfizethetőség (bér/ár arány).  
    Nice-to-have: digitális készségek, bizalmi index (social capital).  
    Fenntarthatóság & kockázati korrekció (RISK ADJUST)  
    Mit mér: pénzügyi, demográfiai, környezeti, energetikai kitettség.  
    Must-have: államadósság/GDP, költségvetési hiány/GDP; nettó kibocsátás/fő trend; demográfiai függőségi ráta; energiaimport-függés (ha nem szerepelt 1)-ben súllyal).  
    Nice-to-have: ökológiai lábnyom, vízkitettség, klíma-adaptációs index.  
    Rezíliencia & koordinációs képesség (ADAPT)  
    Mit mér: kríziskezelés, végrehajtási/koordinációs teljesítmény, társadalmi kohézió.  
    Must-have: vészhelyzeti logisztika-/ellátási mutatók (pl. katasztrófa-reakció idő), oltási/krízis-programok végrehajtási rátája; választási/részvételi stabilitás.  
    Nice-to-have: civil részvétel, önkéntesség, polarizációs indikátorok.  
Hogyan pontozzuk (rövid metodika)  
    Normalizálás: metrikánként 0–100 (min–max) + irányhelyesítés; érzékenység-ellenőrzés kvantil-skálával.  
    Pillér-pont: metrikák súlyozott átlaga (alap: egyenlő súly a must-have-ek között; nice-to-have 0.5x súly).  
    Végpontszám (NHM): ensemble az (i) egyenlő pillérsúly, (ii) PCA(1), (iii) rang-átlag módszerekből.  
    ToC-súlyozás opció: (Input 30%, Process 25%, Output/Outcome 25%, Risk/Adapt 20%) – vagy egyenlő 8×12.5%.  
    Robusztusság: k-fold=10 metrika-dropout (≈20%) + leave-one-pillar/metric-out szenzitivitás + 95% CI.  
    Kockázati levonás: a 7) pillért „penaltyként” is használhatod: NHM_raw − λ·RiskPenalty (λ=0.5–1.0).  
  
**3. Meta-kérdések (ellenőrző kör)**  
* Adj listát a 20 legfontosabb tényezőről, amit mindig figyelembe kell venni egy nemzeti hatékonysági mutatóban.   
* Mely mutatók hiányoznak leggyakrabban a mainstream indexekből?  
* Ha csak 5 dimenziót választhatnál, mi lenne az a mag, amivel kb. 80%-os magyarázóerőt kapunk?  
* Mi az a 10 kevésbé nyilvánvaló tényező, amitől egy ilyen KPI félremehet, ha kihagyjuk?  
👉 Ezek kötelezően a szimuláció előtt, előkészítő lépésként futtatandók.  
  
**4. Adatforrások és operacionalizálás**  
10–12 mérhető mutató kiválasztása publikus, összehasonlítható adatokból.  
Normalizálási logika (globális vagy regionális skála, irányhelyesítés).  
Lehetséges proxyk, ha nincs direkt adat.  
  
**5. Vakfoltok feltárása**  
A modell explicit listázza, mely dimenziók maradnak ki a számításból.  
Rövid kvalitatív becslés: mennyire torzíthatják a végeredményt.  
  
**6. Számítási eljárás**  
* Normalizálás (0–100, irányhelyesítve),  
* Ensemble: egyenlő súly + PCA(1) + rang-átlag → átlagolva.  
* K-fold=10 Cross-Validation: minden foldban véletlen metrika-dropout (≈20%), újraszámolás, majd fold-átlag.  
* Szenzitivitás és interpretálhatóság  
(a) „Mi lenne, ha minden közepes, de X kiugró?” → minden pillér külön lefuttatva. Hatás nagyságának visszajelzése a végső KPI-ra.  
(b) „leave-one-pillar-out” és „leave-one-metric-out” hatás a végpontszámra (Δ pont).  
* Hozzájárulás: egyszerű Shapley-szerű (per-pillér variancia-hozzájárulás)  
* Szórás- és konfidencia intervallum riport  
* Stabilitás-mutatók: fold-átlag, fold-szórás, 95% CI a végpontszámra.  
* Opcionálisan: +Kvantil-alapú normalizálás, Peer-csoport (CEE), ha ezek adnak hozzáadott értéket.  
  
**7. Kimenetek**  
(A) Letölthető CSV(-k) + dokumentált Python kód:  
– futtatható, más által is validálható,  
– kommentelve: mi miért van, input–output logika.  
  
(B) Ha van futtatás: szerver-oldali eredmény  
– dokumentációval együtt: hogyan számolt a modell, milyen forrásokat vett,  
– reprodukálhatóság biztosítása.  
  
**8. Formátum és visszaadott anyag**  
Egyértelműen strukturált output:  
* Végső NHM (0–100) grafikonon is láthatóan,  
* Hozam–kockázat 2D ábra,  
* Pillér-hozzájárulások,  
* Szenzitivitási riport,  
* Vakfolt-lista.  
Dokumentáció a minél teljesebb rekonstruálhatóságot megtámogatandó  

