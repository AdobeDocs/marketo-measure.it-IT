---
unique-page-id: 18874730
description: Scopri Account-Based Marketing (ABM) e come Adobe Marketo Measure aiuta i team di marketing e vendita a eseguire strategie ABM di successo.
title: Panoramica del marketing basato sull’account
exl-id: 2ead69c0-66da-439d-a0ba-25c73c4b308c
feature: Account-based Marketing
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Panoramica del marketing basato sull’account {#account-based-marketing-overview}

Le sezioni seguenti forniscono una breve panoramica di ABM, i componenti della [!DNL Marketo Measure] e come aggiungerla al tuo [!DNL Salesforce] layout di pagina. Per ulteriori informazioni su ABM, consulta Adobe [Blog ABM](https://business.adobe.com/blog/basics/account-based-marketing){target="_blank"}.

Per istruzioni dettagliate sulla configurazione di ABM all&#39;interno del [!DNL Salesforce] istanza, vai a [Impostazione del layout di pagina ABM in Salesforce](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md#setting-up-abm-page-layout-in-salesforce){target="_blank"}.

## Cos’è ABM {#what-is-abm}

Il marketing basato sull&#39;account, ABM, è una strategia di marketing in cui il targeting e la vendita vengono effettuati a società e account nel loro complesso, non solo come individui. [!DNL Marketo Measure] Con la funzionalità di mappatura lead-account e il punteggio di coinvolgimento predittivo, i team di marketing e vendita possono implementare strategie ABM di successo.

Affinché il nostro modello di marketing basato sull’account inizi a essere popolato nel CRM, [!DNL Marketo Measure] ha bisogno che siano soddisfatti i seguenti criteri:

* Il tuo CRM ha bisogno di almeno 25 account che abbiano almeno un’opportunità di vincita chiusa su di essi, per valutare meglio le caratteristiche comuni di un account/opportunità &quot;di successo&quot; per la tua azienda.
* L&#39;altra faccia della medaglia, il tuo CRM ha bisogno di almeno 25 Account senza Opportunità Closed Won (tutti gli opp devono essere in una categoria di fase &quot;Open&quot;, o in una categoria &quot;Closed Lost&quot;) - questo ci aiuta a misurare ciò che rende un conto di livello inferiore nella tua organizzazione.

>[!NOTE]
>
>Gli account &quot;bad&quot; di cui sopra devono essere aperti per almeno 12 mesi senza accumulare un&#39;operazione Closed Won; questa è la linea guida di base per stabilire se un&#39;operazione è diventata obsoleta per gli scopi del modello.

## Mappatura lead-account {#lead-to-account-mapping}

La mappatura lead-account è una parte fondamentale di un approccio ABM efficace. Con la mappatura lead-account, i potenziali clienti o i lead sono raggruppati nello stesso account aziendale in cui interagiscono con il tuo marchio. Questo ti consente di eseguire il targeting e vendere a singoli utenti della stessa azienda in modo coerente. Non sono disponibili [!DNL Salesforce] per iniziare a sfruttare questa funzione. Il [!DNL Marketo Measure] Lead to Account Mapping cinque diversi metodi di corrispondenza:

* Sito Web lead per sito Web account
* Lead del dominio e-mail al dominio del sito web dell’account
* Nome società cliente potenziale al nome account
* Dominio del sito Web da società lead a account
* Corrispondenza del dominio sull&#39;indirizzo e-mail del lead con l&#39;account tramite l&#39;indirizzo e-mail del contatto

>[!NOTE]
>
>Ogni lead tenta di ottenere un abbinamento a un account nell’ordine preferenziale dei metodi di cui sopra. Una volta trovata una corrispondenza, l’AccountId viene immediatamente impostato sul Lead e non viene trovato utilizzando un altro metodo. Se il lead ha già un AccountId valido, viene ignorato.

## Punteggio di coinvolgimento predittivo {#predictive-engagement-score}

Il [!DNL Marketo Measure] Il Predictive Engagement Score (Punteggio di coinvolgimento predittivo), o PES, è un valore dinamico che illustra il coinvolgimento di un particolare account con le tue attività di marketing. Questo punteggio è utile per segmentare gli account da targetizzare. Si tratta di uno strumento prezioso per identificare i conti ed eseguire il targeting in modo più efficace ed efficiente.

Ci sono molti componenti che entrano nell’algoritmo che calcola l’PES. L’attualità e l’età hanno una grande influenza sulle modifiche di punteggio, insieme all’ultima attività punto di contatto o alle visualizzazioni di pagina. Anche l’aggiunta di nuovi contatti a un account ha un impatto su PES. Di seguito è riportato un elenco di alcuni input di PES:

* Numero totale di visualizzazioni di pagina dall’account
* Numero medio di visualizzazioni di pagina
* Numero medio di persone nell’account
* Età di visualizzazione dell’ultima pagina
* Età media delle visualizzazioni di pagina
* Numero di persone nell’account
* Pagine importanti specifiche e se vi è stata una visita negli ultimi 30/60/90 giorni
* Se l&#39;account ha un&#39;offerta persa/vinta chiusa
* Probabilità di chiusura persa/vinta

>[!NOTE]
>
>Potresti notare un livello di &quot;N/A&quot; o &quot;-&quot; (il simbolo del trattino) nel Punteggio di Coinvolgimento Predittivo per alcuni Account.

_Un grado &quot;N/D&quot; significa semplicemente che non ci sono dati sufficienti su quel conto perché il modello possa generare un livello vero - con più dati, alla fine viene dato un livello._
_Un livello di &quot;-&quot; (il simbolo del trattino) significa che questo account deve ancora essere elaborato dal processo ABM, a causa di vincoli di tempo, processi saltati occasionalmente e così via. Se ritieni che un account debba avere un livello, basato su altri account o tempistiche simili, contatta e lascia [!DNL Marketo Measure] lo so._

## Impostazione del layout di pagina ABM in [!DNL Salesforce] {#setting-up-abm-page-layout-in-salesforce}

Per iniziare a utilizzare PES, devi aggiungere il campo PES e l’elenco correlato ai layout di pagina appropriati in [!DNL Salesforce].

1. Accedi a **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Accounts]** > **[!UICONTROL Page Layout]**. Quindi seleziona il layout di pagina da modificare.
1. Vai a [!UICONTROL Fields] e spostare il campo &quot;Punteggio di coinvolgimento predittivo&quot; nella sezione Informazioni account.

   ![](assets/1.png)

1. Infine, vai a [!UICONTROL Related Lists] e spostare l’elenco correlato &quot;Lead&quot; nel layout della pagina.

   ![](assets/2.png)

1. Quindi, passa a **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Leads]** > **[!UICONTROL Page Layout]** e selezionare i layout di pagina appropriati da modificare.
1. Clic **[!UICONTROL Fields]** e aggiungi [!UICONTROL Account] in cui si trova nella pagina.

   ![](assets/3.png)

È tutto pronto!

