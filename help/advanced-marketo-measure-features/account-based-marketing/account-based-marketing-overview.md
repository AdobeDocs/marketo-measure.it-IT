---
unique-page-id: 18874730
description: Panoramica del marketing basato su account - [!DNL Marketo Measure] - Documentazione del prodotto
title: Panoramica del marketing basato su account
exl-id: 2ead69c0-66da-439d-a0ba-25c73c4b308c
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# Panoramica del marketing basato su account {#account-based-marketing-overview}

Di seguito è riportata una breve panoramica di ABM, i componenti di [!DNL Marketo Measure] Funzione ABM e come aggiungerla al tuo [!DNL Salesforce] layout di pagina. Per saperne di più su ABM, consulta [questa pagina](https://www.marketo.com/account-based-marketing/){target=&quot;_blank&quot;}.

Per accedere direttamente alle istruzioni per l’impostazione di ABM all’interno della [!DNL Salesforce] istanza, per favore [fai clic qui](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md#setting-up-abm-page-layout-in-salesforce){target=&quot;_blank&quot;}.

## Cos’è l’ABM {#what-is-abm}

Il marketing basato su account, ABM, è una strategia di marketing in cui ti rivolgi e vendi a aziende e account nel loro insieme, non solo come individui. [!DNL Marketo Measure] aiuta i team di marketing e vendita a eseguire strategie ABM di successo con la funzionalità di mappatura lead-to-account e il punteggio di coinvolgimento predittivo.

Affinché il nostro modello di marketing basato su account inizi a popolarsi nel tuo CRM, [!DNL Marketo Measure] richiede il rispetto dei seguenti criteri:

* Il tuo CRM ha bisogno di almeno 25 account con almeno un&#39;opportunità di chiusura per la tua attività, in modo da poter valutare meglio i comuni di un account/opportunità di &quot;successo&quot; per la tua attività.
* Dall&#39;altro lato della moneta, il CRM ha bisogno di almeno 25 account senza opportunità di vittoria chiusa (tutte le opp devono essere nella nostra categoria stadio &quot;Open&quot;, o in una categoria &quot;Closed Lost&quot; - questo ci aiuta a valutare ciò che rende un conto di livello inferiore nella tua organizzazione.

>[!NOTE]
>
>I suddetti conti &quot;cattivi&quot; devono essere aperti per almeno 12 mesi senza accumulare un opp chiuso; questa è la nostra linea guida di base per stabilire se un Opp è diventato obsoleto ai fini del modello.

## Mappatura lead-to-account {#lead-to-account-mapping}

La mappatura &quot;lead-to-account&quot; è una parte fondamentale di un approccio ABM efficace. Con la mappatura lead-to-account, i potenziali clienti o i lead vengono raggruppati nello stesso account aziendale in cui interagiscono con il tuo marchio. Questo ti consente di eseguire il targeting e vendere a singoli utenti della stessa azienda in modo coerente. Non sono disponibili ulteriori [!DNL Salesforce] configurazione necessaria per iniziare a sfruttare questa funzione. La [!DNL Marketo Measure] Lead to Account Mapping: cinque diversi metodi di corrispondenza:

* Sito Web principale per l&#39;account
* Dominio e-mail lead a dominio sito Web account
* Nome società lead sul nome del conto
* Dominio del sito Web dell&#39;azienda lead
* Corrispondenza del dominio sull&#39;indirizzo e-mail del lead all&#39;account tramite l&#39;indirizzo e-mail del contatto

## Punteggio di coinvolgimento predittivo {#predictive-engagement-score}

La [!DNL Marketo Measure] Punteggio di coinvolgimento predittivo, o PES, è un valore dinamico che illustra il coinvolgimento di un particolare account nelle attività di marketing. Questo punteggio è utile per segmentare gli account a destinazione. Si tratta di uno strumento utile per identificare i conti in modo da mirare in modo più efficace ed efficiente.

Ci sono molti componenti che entrano nell&#39;algoritmo che calcola gli SPI. La recency e l’età hanno una grande influenza sulle modifiche ai punteggi, insieme all’ultima attività del punto di contatto o alle visualizzazioni di pagina. Anche l&#39;aggiunta di nuovi contatti a un account ha un impatto sugli SPI. Di seguito è riportato un elenco di alcuni input di PES:

* Numero totale di visualizzazioni di pagina dall’account
* Numero medio di visualizzazioni di pagina
* Numero medio di persone nel conto
* Età dell’ultima visualizzazione della pagina
* Età media delle visualizzazioni di pagina
* Numero di persone nel conto
* Pagine importanti specifiche e se c&#39;è stata una visita negli ultimi 30/60/90 giorni
* Se il conto ha un&#39;operazione persa/vinta chiusa
* Con quale probabilità verrà chiuso perso/vinto

>[!NOTE]
>
>È possibile notare un livello di &quot;N/A&quot; o &quot;-&quot; (il simbolo del trattino) nel Punteggio di coinvolgimento predittivo per alcuni account.

_Un grado di &quot;N/A&quot; significa semplicemente che non disponiamo ancora di dati sufficienti su quel conto perché il nostro modello generi un vero grado - con più dati, un grado sarà dato alla fine._
_Un grado di &quot;-&quot; (il simbolo del trattino) significa che questo account deve ancora essere elaborato dal nostro processo ABM, a causa di vincoli di tempo, processi occasionalmente persi, ecc. Se ritieni che un account debba avere un grado, in base ad altri account o scadenze simili, contatta e lascia [!DNL Marketo Measure] Lo so._

## Impostazione del layout di pagina ABM in [!DNL Salesforce] {#setting-up-abm-page-layout-in-salesforce}

Per iniziare a utilizzare gli PES, è sufficiente aggiungere il campo PES e l&#39;elenco correlato ai layout di pagina appropriati in [!DNL Salesforce].

1. Passa a **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Accounts]** > **[!UICONTROL Page Layout]**. Quindi seleziona il layout di pagina da modificare.
1. Vai a [!UICONTROL Fields] e sposta il campo &quot;Punteggio di coinvolgimento predittivo&quot; nella sezione Informazioni sull’account .

   ![](assets/1.png)

1. Infine, vai a [!UICONTROL Related Lists] e spostare l&#39;elenco correlato &quot;Lead&quot; nel layout della pagina.

   ![](assets/2.png)

1. Quindi, passa a **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Leads]** > **[!UICONTROL Page Layout]** e selezionare il layout di pagina appropriato da modificare.
1. Fai clic su **[!UICONTROL Fields]** e aggiungi la [!UICONTROL Account] campo in cui viene visualizzata l’adattamento alla pagina.

   ![](assets/3.png)

Siete pronti!

