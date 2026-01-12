---
description: Integrazione dei programmi [!DNL Marketo Engage] - [!DNL Marketo Measure]
title: Integrazione dei programmi [!DNL Marketo Engage]
exl-id: c26087e3-d821-4fe7-bacd-eeaa1530a4b0
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 0%

---


# Integrazione dei programmi [!DNL Marketo Engage] {#marketo-engage-programs-integration}

Attraverso l&#39;integrazione di [!DNL Marketo Measure] con i programmi [!DNL Marketo Engage], i nostri clienti possono iniziare a creare punti di contatto per il tracciamento dell&#39;attribuzione dalle iscrizioni al programma Marketo. Questa funzionalità consente agli addetti al marketing di iniziare a tenere traccia delle iscrizioni ai programmi di e-mail o di coinvolgimento che altrimenti non sarebbero visibili da JavaScript [!DNL Marketo Measure] e dovrebbero essere misurati all&#39;interno del percorso di attribuzione.

## Disponibilità {#availability}

Tutti i livelli.

## Requisiti {#requirements}

* Istanza Marketo di produzione
* Istanza di Production Salesforce o Microsoft Dynamics
* Qualsiasi abbonamento a [!DNL Marketo Measure] a pagamento
* Sincronizzazione utenti Marketo abilitata ([!DNL Marketo Measure] impostazioni)
* Programmi Marketo abilitati ([!DNL Marketo Measure] impostazioni)

## Configurazione {#setup}

**Regole**

1. Per iniziare a impostare le regole per i programmi Marketo, passare a **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Programs]**. Fai clic sull&#39;icona **+** per iniziare a creare la prima regola.

   ![Pagina Impostazioni programmi nell&#39;account Marketo Measure](assets/one.png)

   ![Finestra di dialogo per creare una nuova regola con pulsante di aggiunta](assets/two.png)

1. Facoltativamente, puoi impostare un nome per la regola, se questo contribuisce a tenerne traccia. per definire la regola, seleziona innanzitutto il campo dall’elenco dei campi Programma e Iscrizione al programma. Continua a creare la regola selezionando l’operatore e il valore previsto da verificare.

   ![Generatore di regole con elenco a discesa per la selezione dei campi e opzioni operatore](assets/three.png)

1. Aggiungi un’altra istruzione nella stessa casella per impostare un criterio &quot;e&quot; nella regola oppure fai clic sull’icona + all’esterno della casella per impostare un’istruzione &quot;o&quot;.

   ![Generatore di regole che mostra più condizioni con opzioni logiche e/o](assets/four.png)

1. Scegli la data o il campo data/ora da utilizzare per il mapping alla data del punto di contatto. Per visualizzare l&#39;elenco dei valori disponibili da Marketo, immettere una parentesi graffa `{`. Verranno visualizzati i campi disponibili.

   ![Mappatura campo data con menu a discesa di completamento automatico che mostra i campi disponibili](assets/five.png)

   >[!NOTE]
   >Se la regola desidera acquisire la data attività o la data in cui un membro del programma ha raggiunto uno stato particolare, utilizzare l&#39;integrazione delle attività [!DNL Marketo Engage] e impostare una regola per il tipo di attività &quot;Modifica stato in progressione&quot;.

   ![Configurazione regola completata con mapping e condizioni dei campi](assets/six.png)

La regola completata dovrebbe avere un aspetto simile al seguente:

## Test {#test}

Dopo aver creato alcune regole, è possibile testarle per verificare che l&#39;istruzione corrisponda ai programmi.

1. Per eseguire un test, fare clic sul pulsante **[!UICONTROL TEST]** come illustrato di seguito.

   ![Pulsante Test nell&#39;interfaccia delle regole del programma](assets/seven.png)

1. Verrà visualizzata una finestra modale in cui puoi immettere l’ID del programma da Marketo.

   ![Finestra di dialogo modale di test con campo di input ID programma](assets/eight.png)

   Dopo aver immesso l&#39;ID e aver fatto clic sul pulsante [!UICONTROL Test], il nostro motore di regole esaminerà ogni regola e determinerà se il programma soddisfa o meno una qualsiasi delle regole. Nell&#39;esempio seguente, è possibile vedere che il Programma 1002, denominato [!DNL Marketo Measure] Ebook, ha 5 membri del programma ed è idoneo a causa della regola visualizzata.

   Le regole vengono eseguite su un campione di 5000 membri. Se il programma contiene più di 5000 membri, è possibile che non venga eseguita alcuna verifica della compatibilità di tutti i membri. Questo strumento serve semplicemente come un modo per verificare che le regole siano costruite correttamente.

   ![Risultati del test che mostrano il programma corrispondente con numero di membri](assets/nine.png)

   È possibile fare clic sul conteggio membri per visualizzare un elenco degli ID Marketo People idonei all&#39;interno del programma.

   ![Elenco degli ID Marketo People idonei dai risultati del test](assets/ten.png)

## Mappatura canale {#channel-mapping}

Nell&#39;elenco dei canali del programma Marketo è necessario mappare i valori sui [!DNL Marketo Measure] canali di marketing personalizzati creati in Impostazioni. I punti di contatto generati da questi programmi ereditano i nomi dei canali e dei sottocanali selezionati qui.

1. Per iniziare, passa a **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Offline Channels]**.

1. Nella parte superiore, avrai la possibilità di mappare i tuoi tipi di campagna CRM, quindi di seguito, vedrai le opzioni per i tuoi canali del programma Marketo.

1. Seleziona innanzitutto il canale che deve essere mappato al valore, quindi facoltativamente seleziona il Sottocanale. Al termine, fare clic su **[!UICONTROL Save]** in basso.

   ![Impostazioni canali offline che mostrano le opzioni di mappatura dei canali del programma Marketo](assets/eleven.png)

## Costi del programma {#program-costs}

Attraverso l&#39;importazione dei dati dei programmi Marketo, i costi vengono scaricati automaticamente da Costi periodo e il costo riportato in Marketo viene distribuito nel corso del mese assegnato. Ad esempio, se per gennaio 2021 viene segnalato l’importo di 1000 $, tale importo viene suddiviso in 31 giorni. I costi sono disponibili in [!DNL Marketo Measure Discover].

>[!NOTE]
>
>Marketo Measure supporta un solo inserimento di costo periodo al mese. Per garantire l&#39;importazione di tutti i costi, aggregare il costo mensile totale in un&#39;unica voce. Non sono supportate più voci di costo periodo per lo stesso mese.

## Come funziona {#how-it-works}

**Mappature campi**

<table>
 <colgroup>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <th>biz_ad_campaigns</th>
   <th>Marketo</th>
  </tr>
  <tr>
   <td>ID</td>
   <td>id</td>
  </tr>
  <tr>
   <td>IS_DELETED</td>
   <td>(verifica se il programma esiste ancora tramite API)</td>
  </tr>
  <tr>
   <td><p>NOME</p></td>
   <td>name</td>
  </tr>
 </tbody>
</table>

| biz_campaign_members | Marketo |
|---|---|
| ID | &quot;MarketoProgramMembership&quot;_ProgramId_Lead Id |
| MODIFIED_DATE | updatedAt |
| DATA_CREAZIONE | membershipDate |
| LEAD_ID | ID (iscrizione all’elenco) |
| LEAD_EMAIL | E-mail (iscrizione all’elenco) |
| STATO | progressionStatus |
| HAS_RESPONDED | reachStatus |
| NOME_CAMPAGNA | programName |
| ID_CAMPAGNA | programId |
| CAMPAIGN_TYPE | channel |

## Mappatura cookie {#cookie-mapping}

In seguito all&#39;integrazione di [!DNL Marketo Measure] con Marketo, anche l&#39;ID cookie [!DNL Marketo Measure] è ora mappato e sincronizzato con [!DNL Marketo Munchkin Id]. Questo consente di colmare il divario per attribuire il primo contatto anonimo a una sessione web, anziché attribuire i tocchi FT e LC a un’attività Marketo. Immagina questo scenario:

Mark fa clic su un annuncio di [!DNL Facebook] e arriva a wayneenterprises.com dove viene riciclato con [!DNL Marketo Measure] ID 123 e [!DNL Marketo Munchkin Id] 456. Il modulo non viene compilato.

Il team di marketing di Wayne Enterprises invia un&#39;e-mail esplosiva a lead specifici, uno dei quali è `mark@email.com`.

`mark@email.com` riceve l&#39;e-mail, fa clic su e arriva su wayneenterprises.com. Questa diventa `mark@email.com's` seconda visita a `wayneenterprise.com` con gli stessi ID cookie, ma non è stato compilato alcun modulo, quindi [!DNL Marketo Measure] è ancora un visitatore anonimo.

Il team marketing di Wayne Enterprises crea una regola di attività Marketo per generare punti di contatto per un tipo di attività &quot;Fai clic su e-mail&quot;.

L&#39;implementazione odierna creerebbe un singolo punto di contatto FT e LC per `mark@email.com` dall&#39;attività Marketo dal tipo di attività &quot;Click Email&quot;.

Con questo miglioramento della mappatura dei cookie, il FT tornerebbe indietro e verrebbe accreditato all&#39;annuncio [!DNL Facebook] e il LC verrebbe accreditato all&#39;e-mail.

>[!NOTE]
>Con il comportamento di mappatura dei cookie, potresti trovare alcuni punti di contatto LC provenienti da una visita web. È possibile che un lead sia apparso in Marketo senza alcuna attività associata, quindi [!DNL Marketo Measure] ha scaricato quel lead, ha fatto corrispondere i cookie associati, quindi l&#39;ha tracciato fino alla sessione Web più recente, anche se non c&#39;è stata alcuna attività modulo che ha creato il lead.

## Domande frequenti {#faq}

**Come si imposta la data del punto di contatto come data di progressione o come data in cui la modifica dello stato è avvenuta al membro del programma?**

Se la regola desidera acquisire la data attività o la data in cui un membro del programma ha raggiunto uno stato particolare, utilizzare l&#39;integrazione delle attività [!DNL Marketo Engage] e impostare una regola per il tipo di attività &quot;Modifica stato in progressione&quot;. In caso contrario, l&#39;integrazione dei programmi [!DNL Marketo Engage] rende disponibile solo la data di iscrizione, che è la prima data che ha portato la persona Marketo nel programma, anche se sono presenti più stati.

**Posso ottenere un elenco di selezione delle opzioni di data per il punto di contatto?**

Per attivare il completamento automatico, iniziare immettendo una parentesi graffa `{` nel campo di testo, verranno visualizzati i campi disponibili.

**Se creo regole del programma Marketo e dispongo anche di regole della campagna CRM, verranno conteggiate due volte?**

Dipende dalla definizione della regola, ma forse sì. dovrai valutare il set di regole in modo da non avere regole che coprono un programma e una campagna, perché non verrà deduplicato né rilevato per appartenenze simili. Una soluzione possibile è copiare le regole di Campaign su Programmi se desideri che Marketo sia l’unica fonte di verità, quindi rimuovere le regole di Campaign. Un’altra opzione consiste nell’aggiungere un criterio &quot;CreatedOn&quot; o &quot;CreatedDate&quot; nelle regole in modo che le regole precedenti a una certa data utilizzino le regole di Campaign e quelle successive a una certa data utilizzino le regole di Programma. Ci sono molte soluzioni alternative, ma ci vorrà un po&#39; di pianificazione e coordinamento.

**Sono disponibili campi personalizzati per l&#39;iscrizione al programma Marketo per definire?**

Per il momento non è possibile supportare i campi personalizzati per l’iscrizione al programma a causa di limitazioni tecniche. Una volta che tali campi saranno disponibili tramite API Marketo aggiuntive, saranno esposti a noi e visibili per l’utente.

**Come posso sapere se usare programmi o attività?**

L&#39;integrazione dei programmi [!DNL Marketo Engage] è un modo semplice per generare punti di contatto a seconda che una persona sia o meno membro di un programma. Se ti interessa definire una regola in base al momento in cui una persona cambia in un particolare stato del programma, l&#39;integrazione delle attività [!DNL Marketo Engage] sarà la configurazione desiderata, in particolare il tipo di attività &quot;Modifica stato in progressione&quot;.
