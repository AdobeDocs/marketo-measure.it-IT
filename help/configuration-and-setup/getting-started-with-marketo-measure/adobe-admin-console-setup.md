---
description: Configurazione di Adobe Admin Console - Marketo Measure - Documentazione del prodotto
title: Installazione di Adobe Admin Console
feature: Installation
exl-id: f9edacae-79e0-408c-ac37-bbe67c185f2d
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 1%

---

# Installazione di Adobe Admin Console {#adobe-admin-console-setup}

Il primo passaggio per utilizzare [!DNL Marketo Measure] consiste nel creare e accedere al Adobe Admin Console con provisioning. Se non hai ricevuto l&#39;e-mail con le istruzioni di accesso, contatta il rappresentante del tuo account [!DNL Marketo Measure].

## Configurare il Adobe Admin Console e il provider di identità {#set-up-your-adobe-admin-console-and-identity-provider}

Come prodotto della suite Adobe, [!DNL Marketo Measure] utilizza tutte le funzionalità di Adobe Admin Console per Identity Management. Altre risorse possono essere [trovate qui](https://helpx.adobe.com/it/enterprise/using/admin-console.html).

È consigliabile esaminare le risorse, le best practice e le opzioni disponibili per [Identity Management](https://helpx.adobe.com/it/enterprise/using/set-up-identity.html).

Per informazioni e analisi sulla configurazione dell&#39;Identity Management in Adobe Admin Console, contattare il rappresentante commerciale [!DNL Marketo Measure].

Per facilitare l&#39;autenticazione e l&#39;autorizzazione degli utenti con le istanze di [!DNL Marketo Measure], sono necessari i seguenti passaggi in Adobe Admin Console:

**Configurazione della scheda prodotto [!DNL Marketo Measure]**

Dopo aver effettuato l&#39;accesso a Adobe Admin Console, vengono visualizzate le istanze di prodotto [!DNL Marketo Measure] presenti nella sezione Panoramica.

![](assets/adobe-admin-console-setup-1.png)

Facendo clic sulla scheda prodotto [!DNL Marketo Measure] vengono visualizzate tutte le istanze di [!DNL Marketo Measure]. Per impostazione predefinita, ogni istanza di [!DNL Marketo Measure] ha un proprio profilo con prefisso &#39;[!DNL Marketo Measure]&#39;. Tutti gli amministratori o gli utenti aggiunti a questo o a qualsiasi altro profilo all&#39;interno di questa istanza potranno accedere a [!DNL Marketo Measure].

![](assets/adobe-admin-console-setup-2.png)

Non è richiesta alcuna azione per creare un profilo all&#39;interno delle [!DNL Marketo Measure] istanze di prodotto.

Per iniziare ad aggiungere gli utenti che possono accedere a [!DNL Marketo Measure], consulta la sezione [Aggiunta di [!DNL Marketo Measure] amministratori e [!DNL Marketo Measure] utenti](#adding-marketo-measure-admins-and-marketo-measure-users) di seguito.

## Aggiunta di [!DNL Marketo Measure] amministratori e [!DNL Marketo Measure] utenti {#adding-marketo-measure-admins-and-marketo-measure-users}

Il passaggio successivo consiste nel concedere l&#39;accesso all&#39;applicazione [!DNL Marketo Measure] aggiungendo utenti. Questa operazione può essere eseguita nella directory amministratori e utenti della scheda prodotto [!DNL Marketo Measure].

| Tipo utente | Descrizione |
|---|---|
| Amministratori | si tratta di amministratori e utenti avanzati dell&#39;applicazione [!DNL Marketo Measure] con la piena capacità di aggiornare e gestire le opzioni di configurazione specifiche di [!DNL Marketo Measure] |
| Utenti | si tratta di utenti standard dell&#39;applicazione [!DNL Marketo Measure] con autorizzazioni di sola lettura nell&#39;applicazione [!DNL Marketo Measure] |

Quando si aggiunge un utente al rispettivo gruppo, viene visualizzato il relativo [tipo di identità elencato](https://helpx.adobe.com/it/enterprise/using/set-up-identity.html).

>[!NOTE]
>
>Per essere un amministratore di [!DNL Marketo Measure] (in [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}), è necessario aggiungere un utente come utente _e_ un amministratore a qualsiasi profilo di prodotto [!DNL Marketo Measure] all&#39;interno della scheda prodotto [!DNL Marketo Measure].

**Accesso a[!DNL Marketo Measure]**

Dopo aver aggiunto un utente a un profilo di prodotto, può accedere alle sue istanze di [!DNL Marketo Measure] scegliendo l&#39;opzione **Accedi con Adobe ID** all&#39;indirizzo [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

![](assets/adobe-admin-console-setup-3.png)
