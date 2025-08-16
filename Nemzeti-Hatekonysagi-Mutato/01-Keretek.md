NHM × Theory of Change – 8 pontos „best” keret
==============================================

ToC-leképezés: **Inputok (1–2) → Folyamat/Átalakítás (3–4) → Output/Outcome (5–6) → Kockázati korrekció & Adaptáció (7–8)**

1.  **Erőforrás- és adottságbázis (INPUT)**
    

*   _Mit mér:_ humán, tőke, digitális/infrastruktúra, természeti/energia-adottság.
    
*   _Must-have:_ (i) képzett munkaerő: felsőfokú arány, PISA; (ii) tőkeállomány/fő vagy bruttó állótőke-képzés; (iii) szélessáv + logisztikai index; (iv) energiaimport-függés.
    
*   _Nice-to-have:_ egészségben eltöltött évek, ipari villamosenergia-ár.
    

2.  **Intézményi minőség & jogállamiság (INPUT)**
    

*   _Mit mér:_ kormányzati hatékonyság, közbeszerzés minősége, korrupció-kockázat.
    
*   _Must-have:_ WGI Government Effectiveness, Rule of Law; TI-CPI.
    
*   _Nice-to-have:_ bírósági átfutási idők, közbeszerzési verseny mutatók.
    

3.  **Átalakítási hatékonyság (PROCESS)**
    

*   _Mit mér:_ mennyire fordítja az ország az inputokat versenyképes hozzáadott értékké.
    
*   _Must-have:_ TFP (total factor productivity), GDP/foglalkoztatott (PPP), ipari/ szolgáltatási termelékenység.
    
*   _Nice-to-have:_ ellátási lánc-fordulat (value-added share a kivitelben), állami projektvégrehajtás csúszásráta.
    

4.  **Tudás- és innovációs kapacitás (PROCESS)**
    

*   _Mit mér:_ K+F input→output lánc, tudásáramlás.
    
*   _Must-have:_ GERD %GDP; EPO/PCT szabadalmak/fő vagy tudományos cikkek normalizált idézettsége; startup-intenzitás/fő.
    
*   _Nice-to-have:_ vállalati K+F részaránya; egyetem-ipar co-publications.
    

5.  **Piaci integráció & nemzetközi súly (OUTPUT)**
    

*   _Mit mér:_ globális beágyazottság, forráslehívás, szövetségi leverage.
    
*   _Must-have:_ magas minőségű export aránya (tech- vagy komplexitási index); FDI-készlet/fő; EU-forrás lehívási arány vagy NATO-vállalás teljesítése.
    
*   _Nice-to-have:_ hyperscaler/regionális DC jelenlét, logisztikai hub-mutatók.
    

6.  **Társadalmi kimenetek & jóléti minőség (OUTCOME)**
    

*   _Mit mér:_ az előállított érték „minősége” a lakosság szempontjából.
    
*   _Must-have:_ várható élettartam egészségben; jövedelmi medián/PPP; lakhatási megfizethetőség (bér/ár arány).
    
*   _Nice-to-have:_ digitális készségek, bizalmi index (social capital).
    

7.  **Fenntarthatóság & kockázati korrekció (RISK ADJUST)**
    

*   _Mit mér:_ pénzügyi, demográfiai, környezeti, energetikai kitettség.
    
*   _Must-have:_ államadósság/GDP, költségvetési hiány/GDP; nettó kibocsátás/fő trend; demográfiai függőségi ráta; energiaimport-függés (ha nem szerepelt 1)-ben súllyal).
    
*   _Nice-to-have:_ ökológiai lábnyom, vízkitettség, klíma-adaptációs index.
    

8.  **Rezíliencia & koordinációs képesség (ADAPT)**
    

*   _Mit mér:_ kríziskezelés, végrehajtási/koordinációs teljesítmény, társadalmi kohézió.
    
*   _Must-have:_ vészhelyzeti logisztika-/ellátási mutatók (pl. katasztrófa-reakció idő), oltási/krízis-programok végrehajtási rátája; választási/részvételi stabilitás.
    
*   _Nice-to-have:_ civil részvétel, önkéntesség, polarizációs indikátorok.
    

Hogyan pontozzuk (rövid metodika)
---------------------------------

*   **Normalizálás:** metrikánként 0–100 (min–max) + irányhelyesítés; érzékenység-ellenőrzés kvantil-skálával.
    
*   **Pillér-pont:** metrikák súlyozott átlaga (alap: egyenlő súly a must-have-ek között; nice-to-have 0.5x súly).
    
*   **Végpontszám (NHM):** ensemble az **(i) egyenlő pillérsúly**, **(ii) PCA(1)**, **(iii) rang-átlag** módszerekből.
    
*   **ToC-súlyozás opció:** (Input 30%, Process 25%, Output/Outcome 25%, Risk/Adapt 20%) – vagy egyenlő 8×12.5%.
    
*   **Robusztusság:** k-fold=10 metrika-dropout (≈20%) + leave-one-pillar/metric-out szenzitivitás + 95% CI.
    
*   **Kockázati levonás:** a 7) pillért „penaltyként” is használhatod: NHM\_raw − λ·RiskPenalty (λ=0.5–1.0).
    

Miért „best” ez a 8-as keret?
-----------------------------

*   Teljes ToC-lánc (input→process→output/outcome→risk/adapt), szándék szerint nincsenek nagy vakfoltok, de azért jöhetnek még ötletek.
    
*   Szétválasztja a **potenciált** (1–2) a **képességtől** (3–4), a **piaci/életminőségi eredménytől** (5–6), és mindezt **kockázatra korrigálja** (7), miközben figyeli a **tanuló rendszert** (8).
    
*   Karcsú: 8 blokk × 3 must-have = kb. 24 „kemény” mutatóval már működik; a nice-to-have-ekkel finomhangolható.
    

