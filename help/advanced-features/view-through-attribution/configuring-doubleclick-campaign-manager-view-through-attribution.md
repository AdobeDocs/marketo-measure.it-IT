---
description: Configurazione della vista di Doubleclick Campaign Manager tramite le linee guida di attribuzione per gli utenti di Marketo Measure
title: Configurazione Della Visualizzazione Di Doubleclick Campaign Manager Tramite Attribution
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
feature: Attribution
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Configurazione Della Visualizzazione Di Doubleclick Campaign Manager Tramite Attribution {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Misurazione della vista tramite l&#39;attribuzione {#measuring-view-through-attribution}

>[!IMPORTANT]
>
>A causa di problemi di privacy, i cookie di terze parti sono in uscita. L’annuncio della rimozione dei cookie di terze parti, annunciata nel terzo trimestre 2024 da Google Chrome, segna di fatto la fine di questa forma di tracciamento. Di conseguenza, Adobe rende obsolete le funzioni di Marketo Measure che si basano su cookie di terze parti; in particolare, il tracciamento tra domini diversi e l’attribuzione view-through, che utilizzano il cookie di impression Google/DoubleClick. Nessun’altra funzione di Marketo Measure sarà interessata. Anche l’utilizzo di cookie di prime parti non è interessato. Alla luce della pianificazione di Google, la data prevista di deprecazione per le due funzioni di cui sopra è il 6/1/2024. I dati correlati raccolti prima di questa data rimangono disponibili per i clienti Adobe.

>[!NOTE]
>
>Se utilizzi l&#39;integrazione di [!DNL Marketo Measure] e [!DNL DoubleClick Campaign Manager], è necessaria una [connessione API](/help/api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) per scaricare i dettagli delle campagne e dei creativi per risolvere gli annunci.

Per ottenere un insight più granulare dalla visualizzazione al tracciamento con [!DNL Doubleclick Campaign Manager], è necessario configurare il pixel di tracciamento.

Per ulteriori informazioni sulla funzionalità di visualizzazione tramite attribuzione [!DNL Marketo Measure], fare riferimento a [Domande frequenti su visualizzazione tramite attribuzione Marketo Measure](/help/advanced-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md).

[!DNL Marketo Measure] è considerato un tag piggyback perché è una chiamata di terze parti tramite il tag annuncio DCM. I tag di Piggyback non funzionano con i tag immagine, ma solo con i tag iframe o JavaScript. Secondo il supporto di DCM, ciò non è cambiato di recente ed è sempre stato così. I tag standard sono stati dichiarati obsoleti il 2 ottobre 2017 ma non influiscono sulla capacità di [!DNL Marketo Measure] di tenere traccia delle impression.

Nel caso in cui utilizzi una gerarchia Padre e Figlio in DCM, sarà necessario applicare il tag a tutti i livelli per il tracciamento delle impression.

## Come aggiungere il tag immagine {#how-to-add-the-image-tag}

Aggiungi il tag in Doubleclick sotto l’impostazione dell’inserzionista e crea un tag Impression Event.

1. Aggiungi il seguente codice come pixel immagine 1x1.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Una volta aggiunto, verifica che i delimitatori siano mappati come segue. Questa dovrebbe essere automatica una volta applicato il tag:

   v = %eadv! ID inserzionista [!DNL Expand]\
   a = %eaid! Espandi ID annuncio\
   c = %ecid! Espandi ID Creative\
   s = %esid! Espandi ID sito\
   p = %epid! Espandi ID posizionamento\
   m = %m Macro codice di corrispondenza\
   n = %n Macro numero casuale

   ![](assets/view-attribution-1.png)

## Domande frequenti {#faq}

**Q: il tag immagine è sicuro?**

R: Sì. Non è un tag JavaScript, è un tag immagine.

**D: di quali autorizzazioni ha bisogno l&#39;utente connesso?**

R: dfatrafficking, dfareporting, userinfo.email

**Q: quanto tempo è necessario per importare i dati di spesa?**

R: Fino a 6 ore

**D: quanto tempo ci vuole per importare i dati degli annunci?**

R: Fino a 6 ore
