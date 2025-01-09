---
unique-page-id: 42762749
description: Integrazione attività [!DNL Marketo Engage] - [!DNL Marketo Measure]
title: Integrazione di [!DNL Marketo Engage] attività
exl-id: 463ad9b2-e1bd-49dd-8bf5-0da7b7132f05
feature: Integration
source-git-commit: de366de2d1df3d4dc9fc33e5fd0dab225b6af081
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 0%

---

# Integrazione di [!DNL Marketo Engage] attività {#marketo-engage-activities-integration}

Come parte dell&#39;integrazione complessiva di [!DNL Marketo Measure] e [!DNL Marketo Engage], questo sforzo di richiamare le attività di Marketo svolge un ruolo enorme. Tramite le attività di Marketo, il sistema tiene traccia di eventi come `Click Email`, `Change Score` o `Change Status in Progression`. È possibile analizzare e definire questi tipi di attività per selezionare un sottoinsieme idoneo per i punti di contatto. Una volta creati, i punti di contatto su queste attività vengono tracciati nel percorso di coinvolgimento e misurati insieme agli altri canali di marketing, come Ricerca a pagamento o Marketing dei partner.

## Requisiti {#requirements}

* Istanza Marketo di produzione
* Istanza [!DNL Salesforce] o [!DNL Microsoft Dynamics] di produzione
* Qualsiasi abbonamento a [!DNL Marketo Measure] a pagamento
* Sincronizzazione utenti Marketo abilitata ([!DNL Marketo Measure] impostazioni)
* Programmi Marketo abilitati ([!DNL Marketo Measure] impostazioni)
* Attività Marketo abilitate ([!DNL Marketo Measure] Impostazioni)

## Configurazione {#setup}

1. Per iniziare a configurare le attività di Marketo, passa a **Account personale** > **Impostazioni** > **Attività**.

   ![](assets/one-1.png)

   ![](assets/two-1.png)

   La prima cosa da fare è selezionare l&#39;elenco dei tipi di attività su cui si intende creare le regole. Non è richiesto un numero elevato di tipi di attività, ma è consigliabile non sovraccaricare i punti di contatto e diluire l’importanza di attività cardine significative. Detto questo, non è necessario avere più di cinque tipi di attività per monitorare i progetti rilevanti.

1. Fare clic sul menu a discesa in [!UICONTROL Select Activities Types] per iniziare a scegliere i vari tipi.

   ![](assets/three-1.png)

1. Quando tutte le attività necessarie sono selezionate, puoi visualizzarle compilate in [!UICONTROL Selected Activities List] e in [!UICONTROL Define Rules].

   ![](assets/four-1.png)

1. Per ogni tipo di attività, devi definire una o più regole che determinino quali record sono idonei per i punti di contatto. In questo esempio, aggiungiamo una regola per il tipo di attività &quot;Punteggio di modifica&quot; in modo che il sistema crei un punto di contatto quando una persona Marketo raggiunge un punteggio di 90 o superiore.

1. In primo luogo, a seconda del tipo di attività, potrebbe essere necessario impostare un nome della campagna [!DNL Marketo Measure] che può essere utilizzato successivamente per la mappatura del canale. I nomi delle campagne [!DNL Marketo Measure] possono essere riutilizzati in più regole. Questo consente di avere nomi più ampi che possono essere utilizzati in una regola a canale singolo. Non tutti i tipi di attività contengono un programma Marketo, pertanto è necessario specificare un nome come primo passaggio.

   Ecco un esempio di come apparirebbe quel passaggio aggiuntivo:

   ![](assets/five-1.png)

1. Nell’esempio &quot;Change Score&quot; (Modifica punteggio), è necessario inserire il nome di una campagna poiché tali informazioni vengono estratte dal programma Marketo. Ora crea l’espressione della regola. In questo esempio, selezionare il campo &quot;[!UICONTROL New Value]&quot; con un operatore di &quot;[!UICONTROL is greater than]&quot; con un valore di 90.

   Puoi espandere le regole e aggiungere ulteriori filtri o criteri aggiungendo istruzioni &quot;and&quot; o &quot;or&quot; per limitare i risultati.

   ![](assets/six-1.png)

   ![](assets/seven-1.png)

1. Infine, scegli cosa utilizzare come data del punto di contatto. Tutti i campi data o data/ora disponibili vengono visualizzati qui da Marketo. A meno che tu non abbia campi data personalizzati, vedi &quot;[!UICONTROL Activity Date]&quot;.

   ![](assets/eight-1.png)

1. Assicurarsi di fare clic su **[!UICONTROL Save As Draft]** lungo il percorso in modo da non perdere le modifiche.

   ![](assets/nine-1.png)

1. Passare alla scheda **[!UICONTROL Attribute Mapping]**.

   ![](assets/ten-1.png)

1. Per ogni tipo di attività selezionato, è possibile mappare attributi Marketo aggiuntivi ai campi dei punti di contatto in modo da visualizzare e generare rapporti su tali valori in [!DNL Marketo Measure Discover] o nel CRM.

   Molti campi sono stati mappati automaticamente e non possono essere modificati per coerenza con le altre integrazioni. Fai riferimento alla sezione Mappature campi di seguito per trovare tali valori. Per alcuni tipi di attività, Marketo include attributi per una pagina di destinazione, una pagina di provenienza o un browser che puoi facoltativamente mappare a un campo punto di contatto. Nell’esempio seguente, abbiamo aggiunto alcuni suggerimenti che è possibile rimuovere.

1. Seleziona il campo Buyer Touchpoint dalla colonna sinistra a cui desideri mappare. Quindi, scegli l’attributo Marketo da compilare nel campo Buyer Touchpoint. Ricorda che si tratta di mappature aggiuntive facoltative oltre a quelle già stabilite da [!DNL Marketo Measure].

   Campi mappabili:

   * Città
   * Paese
   * Area geografica
   * Landing Page
   * Pagina referrer
   * Pagina modulo
   * Data modulo
   * Piattaforma
   * Browser

   >[!NOTE]
   >
   >I campi annuncio come Contenuto annuncio o Parola chiave non sono disponibili in questo elenco, in quanto sono riservati per le integrazioni con la piattaforma di annunci.

## Tipi di attività {#activity-types}

Alcuni tipi di attività ci forniscono l’ID e il nome del programma, pertanto è facile mapparli nell’ID e nel nome della campagna su Buyer Touchpoint. Per altri programmi, non esiste alcuna associazione, pertanto parte della definizione delle regole richiede di creare un nome di campagna [!DNL Marketo Measure]. Di seguito sono riportati gli elenchi di ciascuna categoria:

**Tipi di attività con ID programma**

Invia e-mail (6)\
E-mail consegnata (7)\
E-mail non recapitate (8)\
Annulla iscrizione e-mail (9)\
Apri e-mail (10)\
Fai clic su E-mail (11)\
Modifica valore dati (13)\
Modifica punteggio (22)\
Aggiungi all&#39;elenco (24)\
Modifica stato in progressione (104)\
Aggiungi all&#39;alimentazione (113)\
Cambiare la cadenza dello sviluppo (115)

>[!NOTE]
>
>Dei tipi di attività per i quali è previsto un ID programma, se viene rilevata un&#39;attività senza un programma, [!DNL Marketo Measure] non lo accetterà come punto di contatto idoneo perché non è possibile avere valori di Campaign nulli.

**Tipi di attività senza ID programma**

Fai clic sul collegamento (3)\
Nuovo lead (12)\
Sincronizza lead con SFDC (19)\
Converti lead (21)\
Cambia proprietario (23)\
Rimuovi dall’elenco (25)\
Attività SFDC (26)\
E-mail non recapitata morbida (27)\
Elimina lead da SFDC (29)\
Unisci lead (32)\
Aggiungi all’opportunità (34)\
Rimuovi dall’opportunità (35)\
Opportunità di aggiornamento (36)\
Elimina lead (37)\
Invia avviso (38)\
Invia e-mail per vendite (39)\
Apri e-mail per vendite (40)\
Fai clic su E-mail vendita (41)\
Aggiungi a SFDC Campaign (42)\
Rimuovi da SFDC Campaign (43)\
Modifica stato in SFDC Campaign (44)\
Ricevi e-mail per vendite (45)\
Richiedi campagna (47)\
E-mail di vendita non recapitate (48)\
Fase modifica ricavi (101)\
Modifica manualmente fase ricavi (102)\
Cambia segmento (108)\
Chiama webhook (110)\
Inoltro a e-mail amico (111)\
Ricevuto Inoltra a e-mail amico (112)\
Cambia percorso di sviluppo (114)\
Invia lead a Marketo (145)\
Lead di sincronizzazione per Microsoft (300)\
Condividi contenuto (400)
Finestra di dialogo attivata (158)
Documento con cui si interagisce (159)
Appuntamento finestra di dialogo pianificato (160)
Obiettivo Dialogo Raggiunto (161)
Attività personalizzata (xxx)

## Mappatura canale {#channel-mapping}

Per qualsiasi regola appartenente a un Tipo di attività con un ID programma, il Canale del programma Marketo è determinato dal Programma. Il canale del programma viene utilizzato per la mappatura ai tuoi canali offline personalizzati, quindi devi verificare che i tuoi canali siano configurati correttamente [come indicato qui](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#channel-mapping){target="_blank"}.

E per una qualsiasi delle regole da un Tipo di attività senza un ID programma, il primo passaggio era creare un Nome campagna. Utilizza questo nome campagna per configurare i tuoi canali online personalizzati [descritti qui](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md){target="_blank"}.

Se i canali per le attività Marketo non sono configurati correttamente, è probabile che i nuovi punti di contatto rientrino nel canale &quot;Altro&quot;.

## Costi del programma {#program-costs}

Attraverso l&#39;importazione dei dati dei programmi Marketo, i costi vengono scaricati automaticamente da Costi periodo e i costi riportati in Marketo vengono distribuiti nel corso del mese assegnato. Ad esempio, se per gennaio 2021 viene segnalato l’importo di 1000 $, tale importo viene suddiviso in 31 giorni. I costi sono disponibili in [!DNL Marketo Measure Discover].

## Mappatura cookie {#cookie-mapping}

In seguito all&#39;integrazione di [!DNL Marketo Measure] con Marketo, anche l&#39;ID cookie [!DNL Marketo Measure] è ora mappato e sincronizzato con [!DNL Marketo Munchkin Id]. Questo consente di colmare il divario per attribuire il primo contatto anonimo a una sessione web, anziché attribuire i tocchi FT e LC a un’attività Marketo. Immagina questo scenario:

Mark fa clic su un annuncio di Facebook e arriva su wayneenterprises.com dove ottiene un cookie con [!DNL Marketo Measure] ID 123 e [!DNL Marketo Munchkin Id] 456. Il modulo non viene compilato.

Il team di marketing di Wayne Enterprises invia un&#39;e-mail esplosiva a lead specifici, uno dei quali è `mark@email.com`.

`mark@email.com` riceve l&#39;e-mail, fa clic e arriva a `wayneenterprises.com`. Questa diventa `mark@email.com's` seconda visita a `wayneenterprise.com` con gli stessi ID cookie, ma non è stato compilato alcun modulo, quindi [!DNL Marketo Measure] è ancora un visitatore anonimo.

Il team marketing di Wayne Enterprises crea una regola di attività Marketo per generare punti di contatto per un tipo di attività &quot;Fai clic su e-mail&quot;.

L&#39;implementazione odierna creerebbe un singolo punto di contatto FT e LC per `mark@email.com` dall&#39;attività Marketo dal tipo di attività &quot;Click Email&quot;.

Con questo miglioramento della mappatura dei cookie, il FT tornerebbe indietro e verrebbe accreditato all’annuncio Facebook e il LC verrebbe accreditato all’E-mail.

>[!NOTE]
>
>Con il comportamento di mappatura dei cookie, potresti trovare alcuni punti di contatto LC provenienti da una visita web. È possibile che un lead sia apparso in Marketo senza alcuna attività associata, quindi [!DNL Marketo Measure] ha scaricato quel lead, ha fatto corrispondere i cookie associati, quindi l&#39;ha tracciato fino alla sessione Web più recente, anche se non c&#39;è stata alcuna attività modulo che ha creato il lead.

## Domande frequenti {#faq}

**Come posso sapere se creare una regola Programmi di Marketo o una regola Attività di Marketo?**

L&#39;integrazione dei programmi [!DNL Marketo Engage] è un modo semplice per generare punti di contatto in base al fatto che una persona sia membro di un programma. Se si desidera definire una regola in base al momento in cui una persona passa a un determinato stato del programma, l&#39;integrazione delle attività [!DNL Marketo Engage] sarà la configurazione desiderata, in particolare il tipo di attività &quot;Modifica stato in progressione&quot; in modo che la data del punto di contatto possa essere mappata alla data attività generata dal sistema.

**Perché il nome del tipo di punto di contatto è troncato?**

Il campo Tipo di punto di contatto è stato creato nel pacchetto [!DNL Marketo Measure] con 16 caratteri. Sfortunatamente, modificare il limite di caratteri del campo richiederebbe di rendere obsoleto il campo esistente e crearne uno. Il valore del Tipo di punto di contatto è il Tipo di attività, anch’esso impostato nel campo Medium.

**Perché il tipo di attività personalizzato non viene visualizzato nell&#39;elenco delle attività disponibili?**

Mostriamo solo i tipi di attività personalizzati &quot;Approvati&quot; e non Bozza o Approvato con Bozza.

**Come posso determinare per quali tipi di attività voglio generare un punto di contatto?**

Anche se non esiste un limite al numero di tipi di attività che è possibile creare, in genere si consiglia di non più di cinque tipi di attività. Ci vuole tempo per determinare quali attività di marketing sono abbastanza rilevanti da far parte del percorso dei punti di contatto. Ad esempio, &quot;Annulla iscrizione e-mail&quot; potrebbe non essere un punto di contatto significativo da tracciare, ma &quot;Fai clic su e-mail&quot; con filtri aggiuntivi potrebbe essere un buon punto di contatto. Questo varia a seconda dell’organizzazione e di ciascun team, pertanto ti consigliamo di collaborare con il tuo team per trovare l’approccio migliore.

**Perché il nome del browser è stato disattivato?**

Il nome del browser [!DNL Marketo Measure] ha un limite rigido di 20 caratteri, anche se il valore dell&#39;agente utente ottenuto da Marketo tende a essere una stringa più lunga.

BrowserInfo.Name\
BrowserInfo.Version\
PlatformInfo.Name\
PlatformInfo.Version
