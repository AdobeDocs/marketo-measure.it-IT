---
unique-page-id: 37355835
description: Campi punto di contatto - [!DNL Marketo Measure]
title: Campi punto di contatto
exl-id: d6c2bd60-5341-4a52-939a-942afc093306
feature: Touchpoints
source-git-commit: 3424f8a63da40f8762defae1e6ae22ebe60530d0
workflow-type: tm+mt
source-wordcount: '1951'
ht-degree: 0%

---

# Campi punto di contatto {#touchpoint-fields}

Storicamente, quando i clienti sono a bordo con [!DNL Marketo Measure] e nel caso in cui non disponiamo di un&#39;integrazione di tag diretta, il nostro team Customer Success spiega ai clienti come assegnare tag appropriati alle pagine di destinazione in modo che utilizzino il formato UTM corretto e possiamo risolvere i loro annunci. Alcuni di questi clienti non utilizzano UTM, ma utilizzano i propri parametri di assegnazione tag, il che significa che può richiedere molto tempo per modificare tutte le pagine di destinazione in tutte le reti pubblicitarie con una nuova struttura di tag applicata da [!DNL Marketo Measure]. Per adattarci alla loro struttura di tag, ora accettiamo parametri personalizzati che possono essere mappati con le nostre definizioni di regole. L’obiettivo è adattarsi all’utilizzo dei parametri di tracciamento personalizzati da parte dei clienti, in modo da non richiedere loro di modificare la struttura dell’URL.

>[!AVAILABILITY]
>
>Disponibile con segmentazione completa negli abbonamenti di livello 2.

>[!NOTE]
>
>Si tratta di una funzione avanzata che deve essere configurata solo da Professional Services.

## Abilitazione della funzione {#enabling-the-feature}

Dal menu Impostazioni [!DNL Marketo Measure], passare alla pagina Campi punto di contatto. A questo punto è possibile abilitare la funzionalità selezionando **Sì** in **Abilita campi calcolati**. Dopo aver attivato la funzione, puoi creare i campi punto di contatto.

![](assets/one.png)

## Procedura {#how-to}

Per creare un campo calcolato, tieni presente che un utente può eseguire tre azioni diverse: estrae, mappa a e concatena. Questi operatori sono anche noti come operatori per la definizione di un campo calcolato.

### Estratti {#extracts}

L&#39;operatore [!UICONTROL extracts] estrae il valore da un campo da un&#39;altra posizione, ad esempio un campo Campagna, un campo Lead o, in un caso d&#39;uso più avanzato, estrae i parametri personalizzati dalla pagina di destinazione. Viene quindi posizionato in un campo punto di contatto.

**Esempio #1**

È presente un campo personalizzato sul contatto, campaign_source__c, che il cliente desidera rilasciare sul punto di contatto a scopo di reporting. Puoi definire una regola per creare un campo calcolato denominato &quot;Campaign Source&quot; e rilasciare il valore in tale campo.

Obiettivo: utilizza il valore di un campo personalizzato e inseriscilo nell’oggetto punto di contatto per facilitarne la generazione di rapporti.

* Creare un campo calcolato e etichettarlo come &quot;Campaign Source&quot;
* Definisci la regola iniziando con la ricerca del campo Contact.Campaign_Source__c
* Utilizza l’operatore &quot;estrae&quot; perché è necessario estrarre il valore dal parametro
* Per estrarre la stringa completa dal campo, verrà utilizzata l&#39;espressione &quot;(.&#42;)&quot;

   * **(** segna l&#39;inizio dell&#39;estrazione
   * **)** segna la fine dell&#39;estrazione
   * **.&#42;** ci ha detto che stiamo estraendo la stringa completa

![](assets/two.png)

**Esempio #2**

Un caso d’uso comune che questa funzione abilita è quello di estrarre i valori dai parametri personalizzati di una stringa URL. Questa opzione è utile se si utilizzano parametri diversi da UTM ma si desidera analizzare i valori nei campi dei punti di contatto.

**Collegamento:** `https://www.adobe.com/blog/marketing-revenue-reporting-overview?promo=5OFF` o `https://www.adobe.com/blog/marketing-revenue-reporting-overview?promo=25OFF`.\
**Obiettivo:** Creare un campo personalizzato denominato &quot;Codice sconto&quot; e rilasciare il valore &quot;5OFF&quot; o &quot;25OFF&quot;, indipendentemente dal valore passato.

* Creare un campo calcolato e etichettarlo come &quot;Codice sconto&quot;
* Definisci la regola iniziando con la ricerca del campo Touchpoint.Session.LandingPage
* Utilizza l’operatore &quot;estrae&quot; perché è necessario estrarre il valore dal parametro
* Per estrarre il valore della promozione, definiremo il valore come &quot;promo=(\w+)&quot;

   * **(** segna l&#39;inizio dell&#39;estrazione
   * **)** segna la fine dell&#39;estrazione
   * **\w** indica che si sta estraendo una parola che include 0-9
   * **+** estrarrà il valore completo del parametro senza alcun limite di caratteri
   * Tieni presente che stai utilizzando una barra in avanti e non una barra indietro

![](assets/three.png)

**Esempio #3**

Proviamo un esempio simile in cui estraiamo un codice di tracciamento come: `https://www.adobe.com/blog/marketing-revenue-reporting-overview?cid=123456`.

**Obiettivo:** creare un campo calcolato e etichettarlo come &quot;Adobe Campaign Id&quot; con il valore del parametro cid.

* Creare un campo calcolato e assegnargli l’etichetta &quot;Adobe Campaign Id&quot;
* Definisci la regola iniziando con la ricerca del campo Touchpoint.Session.LandingPage
* Utilizza l’operatore &quot;estrae&quot; perché è necessario estrarre il valore dal parametro
* Per estrarre il valore &quot;123456&quot;, definiremo il valore come &quot;cid=(\d{6})&quot;

   * **(** segna l&#39;inizio dell&#39;estrazione
   * **)** segna la fine dell&#39;estrazione
   * **\d** ci ha detto che stiamo estraendo una &quot;cifra&quot;
   * **{6}** è il numero di caratteri che si stanno estraendo

![](assets/four.png)

**Esempio #4**

Man mano che le pagine di destinazione si complicano e si hanno più parametri di tracciamento, potrebbe essere necessario creare più campi di punti di contatto ed estrarre più volte i valori, ad esempio:
`https://www.adobe.com/blog/marketing-revenue-reporting-overview?trackID=123456&country=US&campaign_ID=7890`.

**Obiettivo:** creare più campi calcolati per &quot;Paese di destinazione&quot; e &quot;ID campagna personalizzato&quot; con i rispettivi valori dei parametri.

* Creare un campo calcolato e etichettarlo come &quot;Paese di destinazione&quot;
* Definisci la regola iniziando con la ricerca del campo Touchpoint.Session.LandingPage
* Utilizza l’operatore &quot;estrae&quot; perché è necessario estrarre il valore dal parametro
* Per estrarre il valore &quot;US&quot;, definiremo il valore come &quot;country=(\w{2})&quot;

   * **(** segna l&#39;inizio dell&#39;estrazione
   * **)** segna la fine dell&#39;estrazione
   * **\w** ci ha detto che stiamo estraendo una &quot;parola&quot;
   * **{2}** è il numero di caratteri che si stanno estraendo

* Creare un campo calcolato e etichettarlo come &quot;ID campagna personalizzato&quot;
* Definisci la regola iniziando con la ricerca del campo Touchpoint.Session.LandingPage
* Utilizza l’operatore &quot;estrae&quot; perché è necessario estrarre il valore dal parametro
* Per estrarre il valore &quot;123456&quot;, definiremo il valore come &quot;campaign_ID=(\d{6})&quot;

   * **(** segna l&#39;inizio dell&#39;estrazione
   * **)** segna la fine dell&#39;estrazione
   * **\d** ci ha detto che stiamo estraendo una &quot;cifra&quot;
   * **{6}** è il numero di caratteri che si stanno estraendo

![](assets/five.png)

### Mapping a {#maps-to}

L&#39;operatore [!UICONTROL maps to] crea una tabella di valori da tradurre o inserire in un altro valore. Di solito, si presenta sotto forma di un valore chiave in cui un codice rappresenta un nome descrittivo che deve essere mappato a tale nome.

**Esempio #1**

Sono presenti campagne create per una &quot;promozione di fine estate&quot; e una &quot;promozione del Black Friday&quot; su più canali. Desideri creare un campo calcolato denominato &quot;Iniziativa&quot; e mappare tutti i punti di contatto con una promozione di &quot;fine estate&quot; o &quot;Black Friday&quot; su un valore di Iniziativa come &quot;Promozioni&quot;, oltre ad altri possibili valori.

![](assets/six.png)

**Esempio #2**

Ora che abbiamo imparato a estrarre e mappare i campi, combiniamo queste azioni per estrarre prima un valore da un parametro, quindi mapparlo su un nome descrittivo che abbia un po&#39; più di senso. Iniziamo quindi con questa pagina di destinazione: `https://www.adobe.com/blog/marketing-revenue-reporting-overview?BZ=04-01-09-03-10`.

**Obiettivo:** creare più campi calcolati, dove il primo numero corrisponde a un&#39;area geografica, il secondo a un prodotto, il terzo a un&#39;iniziativa, il quarto a un utente tipo e il quinto a una piattaforma multimediale. Quindi, mappa il valore numerico su un &quot;nome descrittivo&quot;.

* Creare un campo calcolato e etichettarlo come &quot;Area&quot;
* Definisci la regola iniziando con la ricerca del campo Touchpoint.Session.LandingPage
* Utilizza l&#39;operatore &quot;[!UICONTROL extracts]&quot; perché è necessario estrarre il valore dal parametro
* Per estrarre il valore &quot;04&quot;, definiremo il valore come &quot;BZ=(\d{2})-\d{2}-\d{2}-\d{2}-\d{2}&quot;

   * **(** segna l&#39;inizio dell&#39;estrazione

      * Tieni presente che poiché estraiamo solo le 4, solo le prime cifre hanno la parentesi aperta
   * **)** segna la fine dell&#39;estrazione

      * Tieni presente che poiché estraiamo solo le 4, solo le prime cifre hanno la parentesi chiusa
   * **\d** ci ha detto che stiamo estraendo una &quot;cifra&quot;
   * **{2}** è il numero di caratteri che si stanno estraendo



* Fare clic su [!UICONTROL Save]. È necessario salvare il nuovo campo prima che sia disponibile per l&#39;utilizzo per la regola successiva.
* Quindi, è necessario mappare tutti i valori possibili per le prime cifre ai relativi nomi descrittivi
* Creare un campo calcolato e etichettarlo come &quot;Region_Name&quot;
* Definisci la regola iniziando con la ricerca del campo estratto. In questo caso, [!DNL Touchpoint.Region]
* Utilizzare l&#39;operatore &quot;[!UICONTROL maps to]&quot; poiché si desidera creare una mappatura per ogni numero al relativo valore
* Viene visualizzata una tabella in cui elencare ogni mappatura. Alla fine sarà più o meno così:
* In base alla mappatura e all’URL indicati sopra, il &quot;Region_Value&quot; di un punto di contatto con questa pagina di destinazione sarà &quot;EMEA&quot;
* Ripeti l’estrazione e la mappatura per i rimanenti 4 set di cifre

   * Per estrarre 01, è necessario definire il valore come &quot;BZ=\d{2}-**(\d{2})**-\d{2}-\d{2}-\d{2}&quot;
   * Per estrarre il valore 09, è necessario definire il valore come &quot;BZ=\d{2}-\d{2}-**(\d{2})**-\d{2}-\d{2}&quot;
   * Per estrarre lo 03, è necessario definire il valore come &quot;BZ=\d{2}-\d{2}-\d{2}-**(\d{2})**-\d{2}&quot;
   * Per estrarre il valore 10, definire il valore come &quot;BZ=\d{2}-\d{2}-\d{2}-\d{2}-**(\d{2})**&quot;

![](assets/seven.png)

### Concatena {#concatenates}

L&#39;operatore [!UICONTROL concatenates] combina i valori di più campi in un unico campo. Questo è utile per creare un valore personalizzato che richiama i dati tra vari campi al fine di

**Esempio #1**

L’oggetto Opportunity contiene campi separati per Segment__c e Grade__c che l’utente desidera combinare in un singolo campo sull’oggetto Touchpoint a scopo di reporting. Concatenando i campi, verranno visualizzati valori quali Enterprise_A o Mid-Market_B.

![](assets/eight.png)

## Campi e segmenti dei punti di contatto {#touchpoint-fields-and-segments}

Ora che i valori dell’URL sono stati analizzati ed esistono sul punto di contatto, verranno visualizzati i nuovi campi in cui vengono utilizzati i campi del punto di contatto, ad esempio per creare segmenti o definire regole per l’eliminazione dei punti di contatto.

Con questa versione del prodotto è disponibile la possibilità di creare segmenti utilizzando i campi punto di contatto. Impossibile creare i segmenti con campi punto di contatto precedenti.

![](assets/nine.png)

Per semplificare la creazione dei segmenti, ora puoi creare segmenti dinamici dai campi dei punti di contatto creati. Ad esempio, se hai creato un campo punto di contatto che ha analizzato un’area geografica, invece di creare un segmento per ogni possibile area, puoi impostare un segmento e creeremo segmenti per ogni istanza in cui viene visualizzato un nuovo valore. Questa funzione è estremamente utile se un attributo come il codice postale deve essere analizzato e utilizzato come segmento.

La configurazione sarà simile a quella mostrata di seguito. Il Nome segmento richiama dinamicamente il valore del Campo punto di contatto utilizzando le parentesi graffe per cercare il campo.

![](assets/ten.png)

La regola fa riferimento allo stesso campo punto di contatto e cerca valori &quot;non uguali a null&quot;.

![](assets/eleven.png)

## Domande frequenti {#faq}

**Esiste un numero massimo di campi punto di contatto che è possibile creare?**

È previsto un limite di 100 campi.

**Il nuovo campo punto di contatto appena creato nell&#39;elenco a discesa non viene visualizzato. Dov&#39;è?**

Non dimenticare di salvare le regole dopo averle create. Se il nuovo campo non viene visualizzato, verifica se è stato salvato. È necessario salvare il nuovo campo prima che sia disponibile per l&#39;utilizzo per la regola successiva.

>[!NOTE]
>
>A causa del livello di complessità, un campo punto di contatto che utilizza l’operatore &quot;mappa su&quot; non è disponibile per essere utilizzato in un altro campo punto di contatto.

**Espressione utilizzata per estrarre più parametri da una singola pagina di destinazione?**

Come nell’#4 Estrai esempio, è necessario creare più campi per estrarre ciascuno dei parametri. Pertanto, se si dispone di cinque valori diversi, verranno creati cinque campi punto di contatto per estrarre ciascuno di essi.

**Perché non visualizzo i nuovi campi nello schema [!DNL Marketo Measure]?**

È necessario un ulteriore lavoro per esporre i nuovi campi nello schema di Data Warehouse [!DNL Marketo Measure]. Al momento, i campi sono esposti tramite impostazioni e configurazione, in modo da poter utilizzare i campi punto di contatto nella creazione di segmenti o nella creazione di regole per l’eliminazione dei punti di contatto.

**Come posso verificare che la mia espressione di estrazione sia valida e richiamare il valore corretto?**

È disponibile uno strumento online ([[!DNL https]://regex101.com/](https://regex101.com/){target="_blank"}) che è possibile eseguire e verificare l&#39;espressione. L’espressione appare verde se è valida o rossa se non è valida. Inoltre, la casella [!UICONTROL explanation] in alto a destra è utile e indica cosa si sta estraendo.

![](assets/twelve.png)

![](assets/thirteen.png)
