---
unique-page-id: 18874781
description: Configurazione Della Visualizzazione Di Doubleclick Campaign Manager Tramite Attribution - [!DNL Marketo Measure]
title: Configurazione Della Visualizzazione Di Doubleclick Campaign Manager Tramite Attribution
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
feature: Attribution
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Configurazione Della Visualizzazione Di Doubleclick Campaign Manager Tramite Attribution {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Misurazione della vista tramite l&#39;attribuzione {#measuring-view-through-attribution}

>[!NOTE]
>
>Se utilizzi il [!DNL Marketo Measure] e [!DNL DoubleClick Campaign Manager] dell&#39;integrazione, è necessario un [Connessione API](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) così possiamo scaricare i dettagli delle campagne e dei creativi per risolvere gli annunci.

Per ottenere informazioni più granulari dalla visualizzazione fino al tracciamento con [!DNL Doubleclick Campaign Manager], è necessario configurare il pixel di tracciamento.

Per ulteriori informazioni su [!DNL Marketo Measure] Visualizza tramite funzionalità di attribuzione, fare riferimento a [Domande frequenti su Marketo Measure View Through Attribution](/help/advanced-marketo-measure-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md).

[!DNL Marketo Measure] è considerato un tag piggyback perché si tratta di una chiamata di terze parti tramite il tag annuncio DCM. I tag di Piggyback non funzionano con i tag immagine, ma solo con i tag iframe o JavaScript. Secondo il supporto di DCM, ciò non è cambiato di recente ed è sempre stato così. I tag standard sono stati dichiarati obsoleti il 2 ottobre 2017 ma non influiscono sulla capacità di [!DNL Marketo Measure] per tenere traccia delle impression.

Nel caso in cui utilizzi una gerarchia Padre e Figlio in DCM, sarà necessario applicare il tag a tutti i livelli per il tracciamento delle impression.

## Come aggiungere il tag immagine {#how-to-add-the-image-tag}

Aggiungi il tag in Doubleclick sotto l’impostazione dell’inserzionista e crea un tag Impression Event.

1. Aggiungi il seguente codice come pixel immagine 1x1.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Una volta aggiunto, verifica che i delimitatori siano mappati come segue. Questa dovrebbe essere automatica una volta applicato il tag:

   v = %eadv! [!DNL Expand] ID inserzionista\
   a = %eaid! Espandi ID annuncio\
   c = %ecid! Espandi ID creatività\
   s = %esid! Espandi ID sito\
   p = %epid! Espandi ID posizionamento\
   m = %m Macro codice di corrispondenza\
   n = %n Macro numero casuale

   ![](assets/1.png)

## Domande frequenti {#faq}

**D: il tag immagine è sicuro?**

R: Sì. Non è un tag JavaScript, è un tag immagine.

**D: Di quali autorizzazioni ha bisogno l’utente connesso?**

R: dfatrafficking, dfareporting, userinfo.email

**D: Quanto tempo ci vuole per importare i dati di spesa?**

R: Fino a 6 ore

**D: Quanto tempo ci vuole per importare i dati degli annunci?**

R: Fino a 6 ore
