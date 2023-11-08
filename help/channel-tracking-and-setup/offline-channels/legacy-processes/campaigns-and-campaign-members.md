---
unique-page-id: 18874578
description: Campagne e membri della campagna - [!DNL Marketo Measure] - Documentazione del prodotto
title: Campagne e membri della campagna
exl-id: e4e2b154-39ac-4295-a541-7fa6112672e3
feature: Channels
source-git-commit: 38c721d10ac33ae85da1d425b6af53b9e3dfd0a1
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---

# Campagne e membri della campagna {#campaigns-and-campaign-members}

[!DNL Salesforce] Le campagne hanno lo scopo di tenere traccia degli elenchi di lead e contatti associati a un programma o a un’attività di marketing. Si tratta solitamente di webinar, registrazioni o visite allo stand, ad esempio. Gli addetti al marketing possono scegliere se accreditare o meno una campagna in un percorso di punti di contatto.

>[!NOTE]
>
>Questo articolo riguarda un processo obsoleto. Invitiamo gli utenti a utilizzare [processo in-app nuovo e migliorato](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Abilitazione dei punti di contatto {#enabling-touchpoints}

Il [!DNL Marketo Measure] [!DNL Salesforce] Il pacchetto includerà un campo con l’etichetta &quot;Abilita punti di contatto dell’acquirente&quot; sull’oggetto Campaign. Una volta aggiunto il campo al layout di pagina, sarà simile al seguente:

![](assets/1.png)

Le opzioni disponibili nell’elenco a discesa sono:

![](assets/2.png)

* Includi tutti i membri della campagna: ogni lead o contatto aggiunto alla campagna riceverà un punto di contatto associato alla campagna.
* Includi solo i membri della campagna &quot;Rispondenti&quot;: solo i lead o i contatti con lo stato di membro della campagna &quot;Risponduto&quot; riceveranno un punto di contatto associato alla campagna.
* Escludi tutti i membri della campagna: nessuno dei lead o dei contatti riceverà un punto di contatto associato alla campagna.

Tieni presente che i membri della campagna devono avere un indirizzo e-mail associato al proprio record per poter [!DNL Marketo Measure] per creare un punto di contatto. Senza un indirizzo e-mail, [!DNL Marketo Measure] non assegnerà un punto di contatto al membro della campagna.

## Date di sincronizzazione della campagna {#campaign-sync-dates}

Con l&#39;installazione del pacchetto, [!DNL Marketo Measure] includerà anche 2 campi data sull’oggetto Campaign: Data di inizio punto di contatto e Data di fine punto di contatto.

Queste date dicono [!DNL Marketo Measure] quando dovremmo iniziare o interrompere l’inclusione dei membri della campagna dal percorso Campaign al punto di contatto. È possibile impostare una data o entrambe oppure nessuna.

## Caso d’uso per la data di inizio del punto di contatto {#use-case-for-touchpoint-start-date}

La data di inizio può essere utilizzata nel caso in cui una campagna esistente venga utilizzata per il tracciamento di lead e contatti, ma l’utente desidera iniziare a misurare solo dopo che sono stati implementati nuovi sistemi o processi, pertanto decide di impostare una data di inizio una volta [!DNL Marketo Measure] deve iniziare a tenere traccia di tali membri della campagna.

## Caso d’uso per data di fine punto di contatto {#use-case-for-touchpoint-end-date}

Se prima di utilizzare [!DNL Marketo Measure], utilizzavi una piattaforma di automazione marketing che teneva traccia delle interazioni digitali dei lead (invio di moduli IE) e quindi li caricava in una [!DNL Saleforce] Campaign, puoi sfruttare il campo Data di fine punto di contatto. Impostare la data di fine del punto di contatto come data di inizio con [!DNL Marketo Measure] e abilitare i punti di contatto dell’acquirente, l’interazione digitale di ciascuno di questi lead verrà creata come punto di contatto. Il motivo per cui imposterai la data di fine del punto di contatto come data di inizio con [!DNL Marketo Measure] è perché, andando avanti, monitoreremo queste interazioni digitali attraverso il nostro javascript.

![](assets/3.png)

## Membri della campagna {#campaign-members}

I membri della campagna sono nidificati in [!UICONTROL Campaigns]e sono correlati a un lead o a un contatto. Un lead o un contatto può essere aggiunto solo una volta a una campagna, il che può essere problematico a seconda del caso di utilizzo della campagna. Quando una campagna viene sincronizzata, l’iscrizione alla campagna viene utilizzata come un’attività di marketing che viene inserita nel percorso dei punti di contatto e trattata come una compilazione di modulo.

## Stato punto di contatto acquirente {#buyer-touchpoint-status}

Se attivato, [!DNL Marketo Measure] invia un valore di stato al membro della campagna in 4 campi diversi inclusi nel pacchetto installato: Stato del punto di contatto (lead), Stato del punto di contatto (contatto), Stato del punto di contatto (opportunità) e Data dello stato del punto di contatto. Questo consente ai clienti di controllare se un punto di contatto è stato creato come punto di contatto Acquirente o come punto di contatto di attribuzione Acquirente, a seconda dell’oggetto a cui è correlato. La Data stato punto di contatto è semplicemente l’ultima data in cui lo stato è stato aggiornato sul membro della campagna.

![](assets/4.png)

## Data punto di contatto acquirente {#buyer-touchpoint-date}

Con l&#39;installazione del pacchetto, [!DNL Marketo Measure] include anche un campo sul membro della campagna denominato &quot;Data punto di contatto acquirente&quot;. Questo consente all’utente di ignorare la data che [!DNL Marketo Measure] utilizzerebbe per la data del punto di contatto nel record Punto di contatto.

Questo potrebbe essere necessario se un elenco è stato caricato giorni/settimane/mesi dopo che si è verificato effettivamente un evento. Esistono diversi modi per aggiornare tutti i record contemporaneamente, come illustrato di seguito.

![](assets/5.png)

Per sapere se è necessario utilizzare o meno la data di contatto dell&#39;acquirente, ecco come vengono determinate le date in base a [!DNL Marketo Measure] a seconda della [!UICONTROL Sync Type] selezionato per la campagna.

Se il [!UICONTROL Sync Type] è impostato su &quot;Include all Campaign Members&quot; (Includi tutti i membri della campagna), la priorità dell’impostazione della data del punto di contatto è dall’alto verso il basso:

* Data punto di contatto acquirente
* Data di creazione del membro della campagna

Se il [!UICONTROL Sync Type] è impostato su &quot;Include only &#39;Responded&#39; Campaign Members&quot; (Includi solo membri campagna con risposta), la priorità dell’impostazione della data del punto di contatto è dall’alto verso il basso:

* Data punto di contatto acquirente
* Data della prima risposta
   * La prima data di risposta viene impostata automaticamente non appena lo stato diventa &quot;Risposta&quot; ed è uno standard [!DNL Salesforce] campo che non può essere modificato

* Data di creazione del membro della campagna

## Data punto di contatto per aggiornamento in blocco {#bulk-update-touchpoint-date}

La data del punto di contatto per l’aggiornamento in blocco è inclusa nella [!DNL Marketo Measure] [!DNL Salesforce] Il pacchetto e il pulsante devono essere aggiunti al layout della pagina.

![](assets/6.png)

Se è necessario aggiornare un numero elevato di record Membro della campagna, è possibile utilizzare [!UICONTROL Bulk Update Touchpoint Date] per la modifica di massa.

Se esistono casi d’uso specifici che questa interfaccia non copre, puoi anche utilizzare [Caricatore dati](https://dataloader.io/){target="_blank"} per esportare i record, apportare la modifica e caricare nuovamente i record in.

Inizia cercando i record e filtrando quelli per i quali desideri impostare una data di contatto dell&#39;acquirente.

>[!CAUTION]
>
>Una ricerca non funziona, come illustrato nell’esempio seguente. L’interfaccia utente non supporta la ricerca di date di punti di contatto acquirenti nulle (la ricerca seguente non funzionerebbe):

![](assets/7.png)

Se non è necessario utilizzare la ricerca e applicare semplicemente le date a ogni record Membro di Campaign, utilizza la &quot;[!UICONTROL Include All Records]&quot; (vedi la schermata seguente), che controllerà tutti i record su tutte le pagine.

Seleziona la data e l’ora dal selettore calendario. Se si desidera selezionare la data e l&#39;ora correnti, fare clic sulla data/ora visualizzata accanto al selettore calendario.

Dopo aver impostato la data e l’ora, fai clic su **[!UICONTROL Update Selected Records]** per applicare le modifiche.

![](assets/8.png)

## Costi della campagna {#campaign-costs}

Scopri tutto sui costi delle campagne [in questo articolo](/help/marketing-spend/spend-management/crm-campaign-costs.md).

## Rimozione membro della campagna {#campaign-member-removal}

Il modo per [!DNL Marketo Measure] tiene il passo con i record eliminati in Salesforce, sia che vengano eliminati Lead, Account o Opportunità, visualizzandoli nell’API e tenendo traccia di una voce contrassegnata come &quot;IsDeleted&quot;. Sfortunatamente, con i membri della campagna, Salesforce ha introdotto un modo diverso di eliminare questi membri da una campagna e in realtà sono solo contrassegnati come &quot;rimossi&quot; invece di &quot;eliminati&quot;, quindi il problema è che in Salesforce vivevano ancora punti di contatto relativi ai membri della campagna eliminati.

Per risolvere il problema: [!DNL Marketo Measure] ha creato un [!DNL Marketo Measure] Oggetto History e trigger da tenere traccia ogni volta che i membri della campagna vengono rimossi, quindi eliminare il punto di contatto corrispondente. **Sarà necessario [!DNL Marketo Measure] Pacchetto Marketing Analytics V6.15 o versione successiva** per utilizzare questa funzione.

>[!CAUTION]
>
>Tieni presente che questo trigger non tiene traccia dei membri della campagna rimossi in passato, quindi funziona solo in futuro. Se devi rimuovere un numero elevato di punti di contatto dei membri della campagna precedenti, contatta [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Università: Campi oggetto della campagna](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
>
>[[!DNL Marketo Measure] University: mappatura dei canali offline](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
