---
description: Gestione dominio - [!DNL Marketo Measure]
title: Gestione del dominio
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
feature: Integration, Tracking
source-git-commit: 4c68fa08797c252a89ba097c723fb8afee82451f
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Gestione del dominio {#domain-management}

Per tenant abilitati per IMS in esecuzione [!DNL Marketo Measure] nell’interfaccia Experience Cloud, [!DNL Marketo Measure] fornisce un’interfaccia che consente agli utenti di gestire il proprio elenco di domini. [!DNL Marketo Measure] Gli utenti devono prima verificare tutti i domini di cui desiderano tenere traccia in [Adobe Admin Console](https://adminconsole.adobe.com/). Una volta verificati i domini nell’Admin Console, gli utenti possono gestire se [!DNL Marketo Measure] utilizza questi domini per il tracciamento del traffico del sito web.

## Aggiunta di domini in Admin Console {#adding-domains-in-admin-console}

Gli utenti IMS con accesso a Adobe Admin Console possono aggiungere e convalidare i domini di loro proprietà. La convalida del dominio comporta l’aggiunta di un record DNS per ciascun dominio e quindi consente all’Admin Console di verificare tale record.

![](assets/domain-management-1.png)

Le istruzioni per l’aggiunta dei domini sono disponibili nella sezione [Documentazione di Admin Console](https://helpx.adobe.com/enterprise/using/add-domains-directories.html). Una volta aggiunto, il dominio deve essere [collegato a una directory](https://helpx.adobe.com/enterprise/using/add-domains-directories.html#link-domains-to-directoies).

## Gestione dei domini in [!DNL Marketo Measure] {#managing-domains-in-marketo-measure}

Dopo aver aggiunto un dominio nell’Admin Console, [!DNL Marketo Measure] sincronizza regolarmente il record nel database. Questa sincronizzazione viene eseguita di notte e ogni volta che un utente visita il **[!UICONTROL Domains]** pagina in [!DNL Marketo Measure] UI. Per impostazione predefinita, tutti i record che [!DNL Marketo Measure] le importazioni sono disabilitate e il tenant deve abilitare manualmente ogni dominio.

![](assets/domain-management-2.png)

Il giorno **[!UICONTROL Integration]** > **[!UICONTROL Domains]** , l’utente visualizza tutti i domini registrati nell’Admin Console, insieme al relativo stato. Ogni dominio può essere abilitato o disabilitato. Se un dominio è abilitato, [!DNL Marketo Measure] il tracciamento raccoglie tutto il traffico visualizzato su quel dominio. Se un dominio è disabilitato, [!DNL Marketo Measure] ignora il traffico proveniente da tale dominio e non crea punti di contatto o altri dati. [!DNL Marketo Measure] conferma la disattivazione di un dominio e avvisa in caso di ramificazioni:

![](assets/domain-management-3.png)

L’attivazione di un dominio ha un impatto immediato e le modifiche non sono retroattive. In futuro, [!DNL Marketo Measure] rimuoverà i dati dai domini disabilitati dopo un periodo impostato.

## Stati {#statuses}

Gli stati di Admin Console sono suddivisi come segue:

* **CONVALIDATO**: questo dominio è verificato in Admin Console
* **NON VERIFICATO**: questo dominio non è completamente verificato nell’Admin Console e non è idoneo al tracciamento in [!DNL Marketo Measure]
* **NON VALIDO**: il dominio potrebbe essere scaduto o essere stato rimosso dall’Admin Console. Tracciamento dei dati in [!DNL Marketo Measure] è contrassegnato per l’eliminazione
* **LEGACY**: dominio creato in [!DNL Marketo Measure] e non esiste nell’Admin Console

Gli stati di tracciamento possono essere i seguenti:

* **ATTIVO**: [!DNL Marketo Measure] riceve dati da questo dominio
* **DISABILITATO**: questo dominio è disponibile per il tracciamento, ma è disabilitato
* **NON DISPONIBILE**: dominio non disponibile per il tracciamento perché non verificato

Passando il puntatore del mouse su un singolo elemento di stato viene attivata una descrizione che spiega ulteriormente tale stato.

## Domande frequenti {#faq}

**Cosa succede quando un dominio viene rimosso nell’Admin Console?**

Quando un dominio viene rimosso nell’Admin Console, [!DNL Marketo Measure] contrassegna il dominio come eliminato. [!DNL Marketo Measure] interrompe immediatamente il tracciamento del traffico su questo dominio, ma non rimuove i dati raccolti in precedenza.

**Perché non è possibile abilitare un dominio?**

Ci sono diversi motivi per cui un dominio potrebbe non essere consentito per la selezione in questa pagina. Se il dominio non viene convalidato nell’Admin Console, non è disponibile in [!DNL Marketo Measure]. Analogamente, se il dominio è di proprietà di un’organizzazione di Adobi diversa da quella corrente [!DNL Marketo Measure] tenant, potrebbe non essere disponibile per la selezione.

**Come rimuovere un dominio da questo elenco?**

Se in un dominio l&#39;interruttore &quot;abilitato&quot; è disattivato, [!DNL Marketo Measure] la ignora ed è effettivamente rimossa da [!DNL Marketo Measure]. Per rimuovere definitivamente un dominio da [!DNL Marketo Measure], è necessario disattivarlo in [!DNL Marketo Measure], quindi rimuoverlo dall&#39;Admin Console.
