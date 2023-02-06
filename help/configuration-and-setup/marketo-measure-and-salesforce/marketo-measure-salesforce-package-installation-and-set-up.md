---
description: "[!DNL Marketo Measure] Installazione e configurazione del pacchetto Salesforce - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] [!DNL Salesforce] Installazione e configurazione dei pacchetti"
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# [!DNL Marketo Measure] Installazione e configurazione del pacchetto Salesforce {#marketo-measure-salesforce-package-installation-and-set-up}

Prima di installare [!DNL Marketo Measure] [!DNL Salesforce] pacchetto base, è necessario determinare se installarlo prima in un [!DNL Salesforce] sandbox prima di passare all’istanza di produzione Salesforce.

>[!NOTE]
>
>Una volta che [!DNL Marketo Measure] l&#39;account è connesso a un [!DNL Salesforce] istanza di produzione, non è possibile spostarsi all’indietro e connettersi a una sandbox. Inoltre, un [!DNL Marketo Measure] l&#39;account può essere connesso solo a un [!DNL Salesforce] istanza di produzione.

La [!DNL Marketo Measure] Il pacchetto di base contiene:

* 7 Personalizzato [!DNL Marketo Measure] Oggetti
* Personalizzato [!DNL Marketo Measure] Campi
* 25 [!DNL Stock] Rapporti

[!DNL Marketo Measure] è in grado di leggere lo standard [!DNL Salesforce] Oggetti, campi e record, tuttavia, [!DNL Marketo Measure] non aggiornerà mai i dati o li invierà in push. Tutti i dati raccolti dalla [!DNL Marketo Measure] Javascript verrà visualizzato nel [!DNL Marketo Measure] Oggetti e campi personalizzati.

Segui i passaggi seguenti per installare il [!DNL Marketo Measure Salesforce] pacchetto base.

1. Utilizzando un browser in incognito, vai alla [Salesforce Appexchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} e accedi.

1. Installa in [!DNL Marketo Measure] pacchetto in sandbox o produzione.

1. Accedi a [!DNL Salesforce] come amministratore.

1. Seleziona **[!UICONTROL Install]per tutti gli utenti**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. Una volta completata l&#39;installazione, puoi visualizzarla.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

Dopo aver completato l&#39;installazione, puoi aggiornare la [[!DNL Salesforce] layout di pagina](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} con [!DNL Marketo Measure] se desiderato.

>[!NOTE]
>
>Leggi le informazioni [!DNL Marketo Measure] Set di autorizzazioni creati e [come verranno utilizzati](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Installa [!DNL Marketo Measure] Pacchetto dashboard {#install-marketo-measure-dashboard-package}

La [!UICONTROL Dashboard] Il pacchetto di estensione contiene tre dashboard predefiniti. Si consiglia di installare [!UICONTROL within] Produzione per tutti gli utenti.

1. Installa il pacchetto dal [[!DNL Salesforce] Appexchange](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t610000001jI6){target="_blank"}.

1. Seleziona **[!UICONTROL Install for All Users]**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-3.png)

## Creazione di una [!DNL Marketo Measure] Profilo e utente {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] invia e riceve i dati tramite una connessione [!DNL Salesforce] all&#39;interno di [!DNL Marketo Measure] app.

Per inviare i dati dei punti di contatto al tuo [!DNL Salesforce] istanza, l&#39;utente connesso deve avere accesso a [!DNL Marketo Measure] oggetti personalizzati (ad esempio, punto di contatto per l’acquirente e punto di contatto per l’attribuzione dell’acquirente) e standard [!DNL Salesforce] oggetti quali Lead e Contatti.

Crea un [!DNL Marketo Measure] per evitare errori di convalida durante l’invio dei dati a Salesforce.

Passaggio 1: Creare un [!DNL Marketo Measure] profilo

1. Assegna le seguenti autorizzazioni:

* &quot;[!DNL Marketo Measure] Set di autorizzazioni amministratore&quot;
   * Il set di autorizzazioni gestito consente a un amministratore SFDC di creare, leggere, scrivere ed eliminare record da [!DNL Marketo Measure] oggetti.
* &quot;Visualizza e modifica set di autorizzazioni lead convertiti&quot;
   * Ciò consente [!DNL Marketo Measure] per decorare i lead dopo che sono stati convertiti in contatti. Se questo set di autorizzazioni non è abilitato, possono esserci rilevanti lacune nel tracciamento dei dati.

>[!NOTE]
>
>Questo profilo può essere un clone di un profilo amministratore di sistema.

Passaggio 2: Creare un [!DNL Marketo Measure] in modo da poter tenere traccia dell’impatto di [!DNL Marketo Measure] sul tuo [!DNL Salesforce] istanza

1. Assegna il nuovo [!DNL Marketo Measure] Profilo per quell&#39;utente.

1. Abilita &quot;Marketing User&quot; come autorizzazione a livello di utente.

* La [!UICONTROL Marketing User] consente all’utente di creare campagne e utilizzare le procedure guidate per l’importazione di campagne. Se questa opzione non è selezionata, l’utente può visualizzare solo le campagne e la configurazione avanzata della campagna, modificare la cronologia della campagna per un singolo lead o contatto ed eseguire i rapporti sulle campagne. [!DNL Marketo Measure] deve essere in grado di leggere e scrivere sull&#39;oggetto campagna.

Passaggio 3: Escludi questo profilo da tutti gli attivatori, i flussi di lavoro e i processi

Passaggio 4: Accedi al tuo [!DNL Marketo Measure] Account e riautorizza il [!DNL Salesforce] connessione con il nuovo utente

1. Vai su apps.bizible.com e accedi con la nuova produzione di utenti [!DNL Salesforce] credenziali.

1. Seleziona **[!UICONTROL Settings]** all&#39;interno del **[!UICONTROL My Account]** a discesa.

1. Seleziona **[!UICONTROL Connections]** all&#39;interno del **[!UICONTROL Integrations]** raggruppamento.

1. Fai clic sull&#39;icona a forma di chiave a destra della connessione corrente [!DNL Salesforce] connessione e selezionare per **Riautorizzare con Produzione**. Accedi nuovamente con le nuove credenziali utente (se richiesto).
