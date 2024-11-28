Analys av laddtider och användbarhet
=======================

Denna uppgift handlar om att analysera laddningstider och användbarhet för olika webbplatser genom att testa deras prestanda och identifiera möjliga förbättringar.

Urval
-----------------------

Urvalet har gjorts utifrån populära svenska e-handelwebbsidor.
De valda webbplasterna är:
- [Elgiganten](https://www.elgiganten.se/).
- [CDON](https://www.cdon.se).
- [H&M](https://www2.hm.com/sv_se/index.html).

Metod
-----------------------


3 sidor på respektive webbplats väljs ut och analyseras med hjälp av [PageSpeed](https://pagespeed.web.dev), utefter prestanda, tillgänglighet, bästa metoder och SEO.
Dessutom analyseras sidornas laddtid, resurser och storlek med hjälp av safaris inbyggda inspekteringsverktyg från [WebKit](https://webkit.org/web-inspector/network-tab/). Mätningarna görs 3 gånger (utan cache), och därefter tas snittet. 
Alla mätningar som gjorts kan hittas i kalkylarket. Resulterande betyg från Pagespeed har färggivits enligt: 0-49 rött, 50-89 gult, 90-100 grönt. 

Resultat
-----------------------

### **H&M**
![H&M:s webbplats](../assets/img/hm.png)

Överlag får man dålig prestanda på mobil. På dator har man dock bäst betyg sammanslaget. Det höga prestationsbetyget kan relateras med de överlag låga laddningstiderna. 
Vad kommer till resurserna så är samtliga sidor på webbplatsen ganska mäktiga, förmodligen på grund av mängden bilder som laddas. Resursstorlekarna är konsistenta, och de skiljer sig väldigt lite vid omladdningar (utan cache).
Vad man kan samla från pagespeed, så ligger möjliga förbättringar i att: reducera körtid för JavaScript, borttagning av JavaScript och CSS som inte används, förkortning av serverns svarstid, samt att minska påverkan från tredjepartskod (ramverk och så vidare). Dessa förbättringar avser främst mobilprestanda. Det rapporteras även om att man bör unvika att ladda in bilder innan de visas på sidan.
Låga SEO värden beror på att sidan blockerar indexering.
Tillgänglighet och bästa metoder får övergripande höga betyg.

Sammanlagt fick webbplatsens sidor 3 röda, 6 gula och 15 gröna betyg.

### **CDON**
![CDON:s webbplats](../assets/img/cdon.png)

Vad gäller prestanda är den sämre på mobil än på dator, dock är den inte helt felfri på dator heller.
Pagespeed föreslår övergripande både för mobil och dator: att minska första svarstid för huvuddokumentet, minska körningstiden för JavaScript, reducera JavaScript som inte används, unvika för stort DOM-träd, minimering av CSS.
I detta fall kunde man se väldigt höga körningstider för JavaScript, där bland annat en fil tog 17 sekunders processortid. Sett till processortid hade dator mellan 2 och 4 gånger bättre prestanda.
Laddningstider är relativt låga, vilket borde väntas i och med att resurserna är begränsade, men vissa element verkar dröja ut. Bland annat var det svårt att få koncisa resultat på hur många resurser som laddas in och hur stora resurserna är. Antagligen laddas saker in dynamiskt, som med den scrollande fliken som visar olika erbjudanden. I vilket fall som, så kunde antalet resurser ligga och ticka uppåt även när sidan var laddad, utan någon navigering.
Tillgänglighet och bästa metoder får överlag grönt, där SEO får lägre betyg är där indexering blockeras.

Sammanlagt fick webbplatsens sidor 5 röda, 4 gula, och 15 gröna betyg. 

### **Elgiganten**
![Elgigantens webbplats](../assets/img/elgiganten.png)

Vad gäller prestanda är den sämre på mobil än på dator, men man har ganska medelmåttiga betyg på dator också. 
Pagespeed föreslår att man: minskar arbetsbelastningen på modertråden, reducerar CSS och JavaScript som inte används, tar bort resurser som blockerar renderingen, minskar körningstiden för JavaScript, samt att man minskar påverkan från tredjepartskod.
Tillgänglighet och bästa metoder bör möjligtvis ses över. Pagespeed rapporterar bland annat att vissa element saknar överordnade element.
Vad gäller SEO blockerar man indexering på alla sidor som testades, vilet drar ner betyget.
Om man tittar på laddningstid så är den spridd. Kategori-sidan hade lång laddningstid, medan resterande hade relativt låg laddningstid. Lite märkligt är att kategorisidan inte laddar störst resurser, men ändå tar den betydligt längre att ladda.
Antalet resurser skiljer också brett mellan omladdningar på samtliga av webbplatsens sidor. Lämnade man sidan utan att navigera så kunde man se hur resurserna tickade uppåt med tiden.

Sammanlagt fick webbplatsens sidor 4 röda, 13 gula, och 7 gröna betyg.

Analys
-----------------------

<div class="embed-container">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vR2vV7fSfkv0yiRJeSzmOFmLN61vvimfP2dyWNIG3TTmAaGb2AXpMdo586jdNf6bsGER7xfrLgI9zMB/pubhtml?widget=true&amp;headers=false"></iframe>
</div>

Det finns flera gemensamma trender för de 3 webbplatserna. 
Alla webbplatser presterar märkbart sämre på mobil än på dator, vilket återspeglar utmaningen med att optimera för mobila enheter som i regel har mycket mer begränsade resurser. Datorer har i regel tillgång till bättre och snabbare hårdvara, snabbare nätverk och även mer effektiv hantering av cache. 

Vad gäller resurser såg man att CDON:s och Elgigantens resurser kunde ticka uppåt även vid inaktivitet. Det är inte helt självklart om det bara beror på att man dynamiskt laddar in olika erbjudanden eller annonser, eller om det är onödiga resurser som hämtas. Om det handlar om onödiga resurser kan detta leda till onödig belastning på användare och även på servrar som måste hantera dessa förfrågningar.

Samtliga webbplatser hade problem med långa körtider för JavaScript, tillsammans med oanvänd JavaScript och CSS. Det fanns även tecken på att front-end kod inte var helt optimerad, med onödigt stora DOM-träd.
Man kunde även se att många av sidorna blockerar indexering, vilket kan skada prestandan vad gäller synlighet för olika sökmotorer.
Vad gäller tillgänglighet får samtliga sidor övergripande goda betyg. 

Tittar man på summeringarna av alla betyg från PageSpeed så är det svårt att säga att en sida är bättre än någon annan. H&M:s sida sticker ut med mycket bra prestanda för dator, korta laddtider, och koncis användning av resurser. Samtidigt verkar man dock inte använda dynamisk laddning. CDON och Elgiganten har medelmåttig prestanda, men samtidigt använder man dynamisk inladdning. H&M och CDON har båda totalt 15 gröna betyg, där Elgiganten bara har 7. Men det är också inte helt självklart att bedömma en webbplats baserat på detta, då betygen beror på så många faktorer. Använder man resursanvändning, laddtid och betyg kan man göra en rangordning enligt: 

1. H&M. Kort laddtid, överlag bra betyg från SpeedPage. Största nackdelen är stor resursanvändning.
2. CDON. Överlag väldigt nära betygsmässigt till H&M, men längre laddningstider, fastän resurserna är mer begränsade.
3. Elgiganten. Sett till betyg sämst, med avvikande laddningstider, och ganska stor resursanändning.

Valet mellan H&M och CDON är inte helt självklart, då de båda presterar väl. Elgiganten får en ganska självklar 3:e plats.

Sett till ren användning är det ingen av sidorna som är för långsam på någon av webbplatserna. I flesta fallen blir sidorna användbara innan alla resurser är laddade. Man kan tänka sig att en godtycklig laddning för en snabb sida bör ligga kring 3-4 sekunder. Efter det kan man uppfatta sidan som långsam. Överlag klarar sig samtliga sidor inom detta, och det är ingen sida som upplevs för långsam.

Referenser
-----------------------

- [Elgiganten](https://www.elgiganten.se/).
- [CDON](https://www.cdon.se).
- [H&M](https://www2.hm.com/sv_se/index.html)
- [PageSpeed](https://www.pagespeed.web.dev)
- [WebKit](https://www.webkit.org/web-inspector/network-tab/)

Övrigt
-----------------------

Jonatan Lundqvist Silins