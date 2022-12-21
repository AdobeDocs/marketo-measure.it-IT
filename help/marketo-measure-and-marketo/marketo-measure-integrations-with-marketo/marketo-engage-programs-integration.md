---
unique-page-id: 42762729
description: "[!DNL Marketo Engage] Integrazione dei programmi - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Engage] Integrazione dei programmi"
exl-id: c26087e3-d821-4fe7-bacd-eeaa1530a4b0
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 0%

---

# [!DNL Marketo Engage] Integrazione dei programmi {#marketo-engage-programs-integration}

Attraverso il [!DNL Marketo Measure] integrazione con [!DNL Marketo Engage] I nostri clienti possono iniziare a creare punti di contatto per il tracciamento dell’attribuzione dalle iscrizioni al programma Marketo. Questa funzionalità consente agli addetti al marketing di iniziare a monitorare le iscrizioni ai programmi da e-mail o da programmi di coinvolgimento che altrimenti non vengono visti dagli [!DNL Marketo Measure] javascript e deve essere misurato all’interno del percorso di attribuzione.

## Disponibilità {#availability}

Tutti i livelli.

## Requisiti {#requirements}

* Istanza Marketo di produzione
* istanza di Production Salesforce o Microsoft Dynamics
* Qualsiasi pagamento [!DNL Marketo Measure] abbonamento
* Sincronizzazione persone Marketo abilitata ([!DNL Marketo Measure] Impostazioni)
* Programmi Marketo abilitati ([!DNL Marketo Measure] Impostazioni)

## Configurazione {#setup}

**Regole**

1. Per iniziare a impostare le regole sui programmi Marketo, passa a **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Programs]**. Fai clic sul pulsante **+** per iniziare a creare la prima regola.

   ![](assets/one.png)

   ![](assets/two.png)

1. Facoltativamente, puoi impostare un nome per la regola se aiuta a tenerne traccia. Seleziona innanzitutto il campo per definire la regola dall’elenco dei campi Appartenenza a programma e Programma. Continua a generare la regola selezionando l’operatore e il valore previsto da verificare.

   ![](assets/three.png)

1. Aggiungi un’altra istruzione all’interno della stessa casella per impostare un criterio &quot;e&quot; nella regola o fai clic sull’icona + all’esterno della casella per impostare un’istruzione &quot;o&quot;.

   ![](assets/four.png)

1. Scegli il campo data o data/ora da utilizzare per eseguire il mapping alla data del punto di contatto. Per visualizzare l’elenco dei valori disponibili in Marketo, immetti una parentesi graffa `{` e verranno visualizzati i campi disponibili.

   ![](assets/five.png)

   >[!NOTE]
   >
   >Se la regola desidera acquisire la data dell&#39;attività o la data in cui un membro del programma ha raggiunto uno stato particolare, è necessario utilizzare il [!DNL Marketo Engage] Integrazione delle attività e imposta una regola per il tipo di attività &quot;Cambia stato in avanzamento&quot;.

   ![](assets/six.png)

La regola completata deve avere un aspetto simile al seguente:

## Test {#test}

Dopo aver creato alcune regole, è possibile verificare che l&#39;istruzione corrisponda ai programmi.

1. Per eseguire un test, fai clic sul pulsante **[!UICONTROL TEST]** come mostrato di seguito.

   ![](assets/seven.png)

1. Viene visualizzata una finestra modale in cui puoi immettere l’ID del programma da Marketo.

   ![](assets/eight.png)

   Una volta inserito l’ID e fatto clic sul pulsante [!UICONTROL Test] il nostro motore di regole esaminerà ogni regola e determinerà se il programma soddisfa o meno una delle regole. Nell’esempio seguente, puoi vedere il Programma 1002, denominato [!DNL Marketo Measure] Ebook, dispone di 5 membri del programma ed è idoneo a causa della regola visualizzata.

   Le regole vengono eseguite in base alla dimensione del campione di 5000 membri. Se il tuo programma contiene più di 5000 membri, è possibile che non verifichiamo la compatibilità di tutti i membri. Questo strumento serve semplicemente come un modo per controllare le regole sono costruite correttamente.

   ![](assets/nine.png)

   È possibile fare clic su Conteggio membri per visualizzare un elenco degli ID Persone Marketo idonei all&#39;interno del programma.

   ![](assets/ten.png)

## Mappatura del canale {#channel-mapping}

Dall’elenco dei canali di programma Marketo, è necessario mappare i valori al [!DNL Marketo Measure] canali di marketing personalizzati creati in Impostazioni. Tutti i punti di contatto generati da questi programmi erediteranno i nomi dei canali e dei sottocanali selezionati.

1. Inizia passando a **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Offline Channels]**.

1. Nella parte superiore, avrai la possibilità di eseguire la mappatura sui tipi di campagna CRM in uso, quindi nella parte inferiore di seguito vedrai le opzioni per i canali di programma Marketo.

1. Seleziona innanzitutto il Canale da mappare al valore, quindi, facoltativamente, seleziona il Canale secondario. Al termine, fai clic su **[!UICONTROL Save]** in basso.

   ![](assets/eleven.png)

## Costi del programma {#program-costs}

Attraverso l’importazione di dati dei programmi Marketo, i costi vengono scaricati automaticamente da Costi periodo e i costi segnalati in Marketo vengono distribuiti per tutto il mese assegnato. Ad esempio, se per gennaio 2021 viene segnalato $1000, i $1000 vengono suddivisi in 31 giorni. I costi sono reperibili in [!DNL Marketo Measure Discover].

## Come funziona {#how-it-works}

**Mappature dei campi**

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>biz_ad_campagne</th> 
   <th>Marketo</th> 
  </tr> 
  <tr> 
   <td>ID</td> 
   <td>id</td> 
  </tr> 
  <tr> 
   <td>IS_DELETED</td> 
   <td>(controlla se il programma esiste ancora tramite API)</td> 
  </tr> 
  <tr> 
   <td><p>NOME</p></td> 
   <td>name</td> 
  </tr> 
 </tbody> 
</table>

| biz_campaign_Members | Marketo |
|---|---|
| ID | &quot;MarketoProgramMembership&quot;_ProgramId_Lead Id |
| MODIFIED_DATE | updateAt |
| CREATED_DATE | membershipDate |
| LEAD_ID | ID (iscrizione a un elenco) |
| LEAD_EMAIL | Email (iscrizione a un elenco) |
| STATO | progressionStatus |
| HAS_RESPONDED | reachStatus |
| CAMPAIGN_NAME | programName |
| CAMPAIGN_ID | programId |
| CAMPAIGN_TYPE | canale |

## Mappatura dei cookie {#cookie-mapping}

Come risultato della [!DNL Marketo Measure] integrazione con Marketo, [!DNL Marketo Measure] Anche l’ID cookie è ora mappato e sincronizzato con il [!DNL Marketo Munchkin Id]. Questo aiuta a colmare il gap per attribuire il primo tocco anonimo a una sessione web invece di attribuire sia il contatto FT che LC a un&#39;attività Marketo. Immaginate questo scenario:

Contrassegnare i clic su un [!DNL Facebook] e atterra su wayneprises.com dove viene cucinato con [!DNL Marketo Measure] ID 123 e [!DNL Marketo Munchkin Id] 456 Non viene compilato alcun modulo.

Il team di Wayne Enterprises Marketing invia un&#39;e-mail esplosiva a specifici lead mirati, uno dei quali è `mark@email.com`.

`mark@email.com` riceve l&#39;e-mail e i clic attraverso e arriva su wayneprises.com. Questo diventa `mark@email.com's` seconda visita a `wayneenterprise.com` con gli stessi ID cookie, ma non è stato compilato alcun modulo, quindi [!DNL Marketo Measure], sono ancora un visitatore anonimo.

Il team di Wayne Enterprises Marketing crea una regola di attività Marketo per generare punti di contatto per un tipo di attività &quot;Click Email&quot;.

L&#39;implementazione odierna creerebbe un unico punto di contatto FT e LC per `mark@email.com` dall’attività Marketo dal tipo di attività &quot;Fai clic su e-mail&quot;.

Con questo miglioramento della mappatura dei cookie, l&#39;FT tornerebbe indietro e ottenere accreditato al [!DNL Facebook] l&#39;annuncio e la LC sarebbero accreditati all&#39;Email.

>[!NOTE]
>
>Con il comportamento di mappatura dei cookie, potresti trovare alcuni punti di contatto LC che provengono da una visita web. È possibile che un lead sia apparso in Marketo senza alcuna attività associata, quindi [!DNL Marketo Measure] il lead è stato scaricato e i cookie associati sono stati confrontati con la sessione Web più recente, anche se non vi era alcuna attività del modulo che ha creato il lead.

## Domande frequenti {#faq}

**Come posso impostare la data del punto di contatto come data di avanzamento o data in cui la modifica dello stato è avvenuta al membro del programma?**

Se la regola desidera acquisire la data dell&#39;attività o la data in cui un membro del programma ha raggiunto uno stato particolare, è necessario utilizzare il [!DNL Marketo Engage] Integrazione delle attività e imposta una regola per il tipo di attività &quot;Cambia stato in avanzamento&quot;. In caso contrario, la [!DNL Marketo Engage] L&#39;integrazione di programmi rende disponibile solo la data di iscrizione, che è la prima data che ha portato la persona Marketo nel programma, anche in presenza di più stati.

**È possibile ottenere un elenco a discesa delle opzioni di data per la data del punto di contatto?**

Per attivare il completamento automatico, inizia inserendo una parentesi graffa `{` nel campo di testo vengono visualizzati i campi disponibili.

**Se creo regole del programma Marketo e dispongo anche di regole della campagna di gestione delle relazioni con i clienti, verranno conteggiate due volte?**

Dipende dalla definizione della regola, ma forse sì. È necessario valutare il set di regole in modo da non disporre di regole che coprano un programma e una campagna, in quanto non verranno deduplicate o rilevate appartenenze simili. Una possibile soluzione è quella di copiare le regole di Campaign in Programmi se desideri che Marketo sia l’unica fonte di verità, quindi rimuovere le regole di Campaign. Un’altra opzione consiste nell’aggiungere nelle regole un criterio &quot;CreatedOn&quot; o &quot;CreatedDate&quot;, in modo che le regole precedenti a una data utilizzino le regole e le regole di Campaign dopo una determinata data utilizzino le regole di Programma. Ci sono molte soluzioni là fuori, ma ci vorrà un po&#39; di pianificazione e coordinamento.

**Sono disponibili campi personalizzati per l’appartenenza al programma Marketo per definire?**

A causa di limitazioni tecniche, per il momento non è possibile supportare i campi personalizzati di appartenenza al programma. Una volta che tali campi saranno disponibili tramite API Marketo aggiuntive, saranno esposti a noi e visibili da usare.

**Come posso sapere se utilizzare Programmi o Attività?**

La [!DNL Marketo Engage] L’integrazione dei programmi è un modo semplice per generare punti di contatto in base al fatto che una Persona sia o meno un membro del programma di un programma. Se sei interessato a definire una regola basata sul momento in cui una Persona cambia in uno specifico stato del Programma, la [!DNL Marketo Engage] L&#39;integrazione delle attività sarà la configurazione desiderata, in particolare il tipo di attività &quot;Cambia stato in progressione&quot;.
