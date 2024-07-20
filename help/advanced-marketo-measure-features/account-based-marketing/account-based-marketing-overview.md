---
unique-page-id: 18874730
description: Scopri Account-Based Marketing (ABM) e come Adobe Marketo Measure aiuta i team di marketing e vendita a eseguire strategie ABM di successo.
title: Panoramica del marketing basato sull’account
exl-id: 2ead69c0-66da-439d-a0ba-25c73c4b308c
feature: Account-based Marketing
source-git-commit: e2165fea3e76baeedf9b22247d005578d6c6da5d
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Panoramica del marketing basato sull’account {#account-based-marketing-overview}

Le sezioni seguenti forniscono una breve panoramica di ABM, dei componenti della funzionalità ABM [!DNL Marketo Measure] e di come aggiungerla al layout di pagina [!DNL Salesforce]. Per ulteriori informazioni su ABM, consulta il [blog ABM](https://business.adobe.com/blog/basics/account-based-marketing){target="_blank"} dell&#39;Adobe.

Per istruzioni dettagliate sulla configurazione di ABM nell&#39;istanza [!DNL Salesforce], vai a [Configurazione del layout di pagina ABM in Salesforce](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md#setting-up-abm-page-layout-in-salesforce){target="_blank"}.

## Cos’è ABM {#what-is-abm}

Il marketing basato sull&#39;account, ABM, è una strategia di marketing in cui il targeting e la vendita vengono effettuati a società e account nel loro complesso, non solo come individui. [!DNL Marketo Measure] consente ai team di marketing e vendite di eseguire strategie ABM di successo con la funzionalità di mappatura lead-account e il punteggio di coinvolgimento predittivo.

Affinché il modello di marketing basato sull&#39;account possa iniziare a essere popolato nel CRM, [!DNL Marketo Measure] deve soddisfare i seguenti criteri:

* Il tuo CRM ha bisogno di almeno 25 account che abbiano almeno un’opportunità di vincita chiusa su di essi, per valutare meglio le caratteristiche comuni di un account/opportunità &quot;di successo&quot; per la tua azienda.
* L&#39;altra faccia della medaglia, il tuo CRM ha bisogno di almeno 25 Account senza Opportunità Closed Won (tutti gli opp devono essere in una categoria di fase &quot;Open&quot;, o in una categoria &quot;Closed Lost&quot;) - questo ci aiuta a misurare ciò che rende un conto di livello inferiore nella tua organizzazione.

>[!NOTE]
>
>Gli account &quot;bad&quot; di cui sopra devono essere aperti per almeno 12 mesi senza accumulare un&#39;operazione Closed Won; questa è la linea guida di base per stabilire se un&#39;operazione è diventata obsoleta per gli scopi del modello.

## Mappatura lead-account {#lead-to-account-mapping}

La mappatura lead-account è una parte fondamentale di un approccio ABM efficace. Con la mappatura lead-account, i potenziali clienti o i lead sono raggruppati nello stesso account aziendale in cui interagiscono con il tuo marchio. Questo ti consente di eseguire il targeting e vendere a singoli utenti della stessa azienda in modo coerente. Non è necessaria alcuna configurazione [!DNL Salesforce] aggiuntiva per iniziare a beneficiare di questa funzione. [!DNL Marketo Measure] ha portato al mapping account diversi metodi di corrispondenza:

* Sito Web lead per sito Web account
* Lead del dominio e-mail al dominio del sito web dell’account
* Nome società cliente potenziale al nome account
* Dominio del sito Web da società lead a account
* Lead del sito Web al dominio e-mail dei contatti dell&#39;account
* Dominio e-mail lead nel dominio e-mail dei contatti dell’account
* Lead del sito Web al dominio e-mail dei lead dell&#39;account
* Dominio e-mail lead nel dominio e-mail dei lead dell’account

I lead/contatti degli account vengono convalidati dai domini e-mail/sito Web e confrontati con il dominio o sottodominio dell’e-mail/sito Web del lead. Viene utilizzato l’account con più corrispondenze.

>[!NOTE]
>
>Ogni lead tenta di ottenere un abbinamento a un account nell’ordine preferenziale dei metodi di cui sopra. Una volta trovata una corrispondenza, l’AccountId viene immediatamente impostato sul Lead e non viene trovato utilizzando un altro metodo.

## Punteggio di coinvolgimento predittivo {#predictive-engagement-score}

Il punteggio di coinvolgimento predittivo [!DNL Marketo Measure], o PES, è un valore dinamico che illustra il coinvolgimento di un particolare account con le attività di marketing. Questo punteggio è utile per segmentare gli account da targetizzare. Si tratta di uno strumento prezioso per identificare i conti ed eseguire il targeting in modo più efficace ed efficiente.

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

_Un livello &quot;N/D&quot; significa semplicemente che non sono disponibili dati sufficienti in tale account per consentire al modello di generare un livello effettivo. Con più dati, alla fine verrà assegnato un livello._
_Un livello di &quot;-&quot; (il simbolo del trattino) indica che questo account deve ancora essere elaborato dal processo ABM, a causa di vincoli di tempo, processi saltati occasionalmente e così via. Se ritieni che un account debba avere un livello, basato su altri account o intervalli di tempo simili, contatta e informa [!DNL Marketo Measure]._

## Impostazione del layout di pagina ABM in [!DNL Salesforce] {#setting-up-abm-page-layout-in-salesforce}

Per iniziare a utilizzare PES, è necessario aggiungere il campo PES e l&#39;elenco correlato ai layout di pagina appropriati in [!DNL Salesforce].

1. Passa a **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Accounts]** > **[!UICONTROL Page Layout]**. Quindi seleziona il layout di pagina da modificare.
1. Vai a [!UICONTROL Fields] e sposta il campo &quot;Punteggio di coinvolgimento predittivo&quot; nella sezione Informazioni account.

   ![](assets/1.png)

1. Infine, vai a [!UICONTROL Related Lists] e sposta l&#39;elenco correlato &quot;Lead&quot; nel layout della pagina.

   ![](assets/2.png)

1. Passare quindi a **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Leads]** > **[!UICONTROL Page Layout]** e selezionare i layout di pagina appropriati da modificare.
1. Fai clic su **[!UICONTROL Fields]** e aggiungi il campo [!UICONTROL Account] che si adatta alla pagina.

   ![](assets/3.png)

È tutto pronto!

