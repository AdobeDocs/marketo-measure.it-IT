---
unique-page-id: 18874781
description: Configurazione della visualizzazione di Doubleclick Campaign Manager tramite attribuzione - [!DNL Marketo Measure] - Documentazione del prodotto
title: Configurazione della visualizzazione di Double Campaign Manager tramite l’attribuzione
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Configurazione della visualizzazione di Double Campaign Manager tramite l’attribuzione {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Misurazione della vista tramite attribuzione {#measuring-view-through-attribution}

>[!NOTE]
>
>Se utilizzi il [!DNL Marketo Measure] e l’integrazione con DoubleClick Campaign Manager richiedono un [Connessione API](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) possiamo scaricare i dettagli delle campagne e dei creativi per risolvere gli annunci.

Per iniziare a ottenere informazioni più granulari dalla visualizzazione tramite il tracciamento con Doubleclick Campaign Manager, il nostro pixel di tracciamento deve essere configurato.

Per favore [fai clic qui](/help/advanced-marketo-measure-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md) per ulteriori informazioni sulle [!DNL Marketo Measure] Funzionalità View Through Attribution.

[!DNL Marketo Measure] è considerato un tag di tipo piggyback perché è una chiamata di terze parti tramite il tag di annunci DCM. I tag Piggyback non funzionano con i tag immagine, ma solo con i tag iframe o javascript. Secondo il supporto DCM, questo non è cambiato di recente ed è sempre stato così. I tag standard sono stati dichiarati obsoleti il 2 ottobre 2017 ma non influiscono sulla capacità di [!DNL Marketo Measure] per tenere traccia delle impression.

Nel caso in cui sfrutti una gerarchia Genitore e Figlio in DCM, il tag deve essere applicato a tutti i livelli per il tracciamento delle impression.

## Aggiungere il tag immagine {#how-to-add-the-image-tag}

Aggiungerai il tag in Doubleclick sotto l’impostazione Inserzionista e vorrai creare un tag evento di impression.

1. Aggiungi il codice seguente come pixel immagine 1x1.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Una volta aggiunto, conferma che i delimitatori sono mappati come segue. Questa deve essere automatica una volta applicato il tag :

   v = %eadv! Espandi ID inserzionista\
   a = %eaid! Espandi ID annuncio\
   c = %ecid! Espandi Creative Id\
   s = %esid! Espandi ID sito\
   p = %epid! Espandi ID posizionamento\
   m = %m Macro codice di corrispondenza\
   n = %n Macro numero casuale

   ![](assets/1.png)

## Domande frequenti {#faq}

**D: Il tag immagine è sicuro?**

R: Sì. Non è un tag JavaScript, è un tag immagine.

**D: Di quali autorizzazioni ha bisogno l&#39;utente connesso?**

R: dfatrafficing, scoraggiare, userinfo.email

**D: Quanto tempo può essere necessario per importare i dati di spesa?**

R: Fino a 6 ore

**D: Quanto tempo può essere necessario per importare i dati degli annunci?**

R: Fino a 6 ore
