---
description: Configurazione di Adobe Admin Console - Marketo Measure - Documentazione del prodotto
title: Installazione di Adobe Admin Console
feature: Installation
exl-id: f9edacae-79e0-408c-ac37-bbe67c185f2d
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Installazione di Adobe Admin Console {#adobe-admin-console-setup}

Il primo passaggio per utilizzare [!DNL Marketo Measure] : per creare e accedere al Adobe Admin Console con provisioning. Se non hai ricevuto l’e-mail con le istruzioni di accesso, contatta il tuo [!DNL Marketo Measure] Rappresentante dell’account.

## Configurare il Adobe Admin Console e il provider di identità {#set-up-your-adobe-admin-console-and-identity-provider}

Come prodotto all’interno della suite Adobe, [!DNL Marketo Measure] utilizza tutte le funzionalità di Adobe Admin Console per Identity Management. Altre risorse possono essere [trovato qui](https://helpx.adobe.com/it/enterprise/using/admin-console.html).

È consigliabile esaminare le risorse, le best practice e le opzioni disponibili per [Identity Management](https://helpx.adobe.com/enterprise/using/set-up-identity.html).

Per informazioni e indicazioni sulla configurazione dell’Identity Management in Adobe Admin Console, contatta il tuo [!DNL Marketo Measure] Rappresentante dell’account.

Per facilitare l&#39;autenticazione e l&#39;autorizzazione degli utenti con [!DNL Marketo Measure] istanze, sono necessari i seguenti passaggi all’interno di Adobe Admin Console:

**Configurazione di [!DNL Marketo Measure] Scheda prodotto**

Dopo aver effettuato l’accesso a Adobe Admin Console, vengono visualizzati i [!DNL Marketo Measure] Istanze di prodotto presenti nella sezione Panoramica.

![](assets/adobe-admin-console-setup-1.png)

Facendo clic su [!DNL Marketo Measure] La scheda prodotto mostra tutte le [!DNL Marketo Measure] istanze. Per impostazione predefinita, ogni [!DNL Marketo Measure] L’istanza ha un proprio profilo con prefisso &quot;[!DNL Marketo Measure]&quot;. Tutti gli amministratori o gli utenti aggiunti a questo o a qualsiasi altro profilo all’interno di questa istanza potranno accedere a [!DNL Marketo Measure].

![](assets/adobe-admin-console-setup-2.png)

Non è richiesta alcuna azione per creare un profilo all’interno del [!DNL Marketo Measure] Istanze del prodotto.

Per iniziare ad aggiungere gli utenti che possono accedere [!DNL Marketo Measure], fare riferimento a [Aggiunta [!DNL Marketo Measure] Amministratori e [!DNL Marketo Measure] Utenti](#adding-marketo-measure-admins-and-marketo-measure-users) sezione successiva.

## Aggiunta [!DNL Marketo Measure] Amministratori e [!DNL Marketo Measure] Utenti {#adding-marketo-measure-admins-and-marketo-measure-users}

Il passaggio successivo consiste nel concedere l&#39;accesso al [!DNL Marketo Measure] mediante l&#39;aggiunta di utenti. Questa operazione può essere eseguita nella directory amministratori e utenti di [!DNL Marketo Measure] scheda prodotto.

| Tipo utente | Descrizione |
|---|---|
| Amministratori | si tratta di amministratori e utenti avanzati [!DNL Marketo Measure] Applicazione con piena capacità di aggiornamento e gestione [!DNL Marketo Measure]opzioni di configurazione specifiche di |
| Utenti | si tratta di utenti standard di [!DNL Marketo Measure] Applicazione con autorizzazioni di sola lettura all&#39;interno del [!DNL Marketo Measure] applicazione |

Quando si aggiunge un utente al rispettivo gruppo, vengono visualizzati i relativi [Tipo di identità elencato](https://helpx.adobe.com/enterprise/using/set-up-identity.html).

>[!NOTE]
>
>Essere un [!DNL Marketo Measure] amministratore (in [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}), un utente deve essere aggiunto come Utente _e_ un amministratore in qualsiasi [!DNL Marketo Measure] profilo di prodotto all’interno di [!DNL Marketo Measure] scheda prodotto.

**Accesso a[!DNL Marketo Measure]**

Dopo che un utente è stato aggiunto a un profilo di prodotto, può accedere al suo [!DNL Marketo Measure] istanze scegliendo il **Accedi con Adobe ID** opzione a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

![](assets/adobe-admin-console-setup-3.png)
