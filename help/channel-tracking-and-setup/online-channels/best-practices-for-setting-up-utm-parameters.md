---
unique-page-id: 18874732
description: Best practice per l’impostazione dei parametri UTM - [!DNL Marketo Measure] - Documentazione del prodotto
title: Procedure consigliate per l’impostazione dei parametri UTM
exl-id: 56019f41-b6ba-48c1-9bef-2a5f56d2d5f4
source-git-commit: 51397a02872035fef41d308c1f855bcaecc29c4e
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# Procedure consigliate per l’impostazione dei parametri UTM {#best-practices-for-setting-up-utm-parameters}

I parametri UTM sono un ottimo modo per suddividere i dati di marketing. [!DNL Marketo Measure] utilizza e acquisisce tutti i parametri UTM per compilare i campi in Salesforce e in [!DNL Marketo Measure] app. Con queste informazioni, sarai in grado di ottenere una comprensione granulare di da dove provengono i tuoi lead, opportunità e offerte chiuse/vinte.

È possibile utilizzare [Generatore URL Google](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"} to set up your UTM parameters and add them to your links within your marketing efforts. Use this [Google Spreadsheet](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"} se si desidera un modo più semplice per tenere traccia di tutti i collegamenti UTM.

## Valori di livello elevato per ciascun parametro {#high-level-values-for-each-parameter}

**utm_medium**: Questo campo viene mappato sul campo Medio. Utilizza utm_medium per indicare il canale di alto livello.

Ad esempio, [!UICONTROL Social], CPC, e-mail, web, organico

Non utilizzare questo campo per richiamare il canale secondario.

**utm_source**: Questo campo è associato al campo Origine punto di contatto. Utilizza utm_source per definire il canale secondario da cui proviene il lead.

Ad esempio, Facebook, Twitter, Linkedin, Drip_email, Email_blast, newsletter.

La tenga semplice. Non utilizzare questo parametro per indicare il tipo di annuncio, come retargeting, sponsorizzato, ecc. Non aggiungere un utm_source = homepage, webdirect, sito web. [!DNL Marketo Measure] compilerà automaticamente queste informazioni per te.

**utm_campaign**: Questo campo viene mappato su Nome campagna pubblicitaria. Utilizza utm_campaign per indicare il titolo della campagna così come esiste nella piattaforma di annunci, o come viene fatto riferimento internamente.

Questo è anche un buon parametro per indicare il tipo di rete Geolocalizzazione, Ad (visualizzazione v. search), ecc.

È consigliabile utilizzare caratteri di sottolineatura invece degli spazi ed evitare di utilizzare la punteggiatura. Questo riduce le possibilità di codifica degli errori da parte dei browser durante la lettura dei parametri.

Ad esempio, AU_Idea_for_an_App_50k

**utm_content**: Viene mappato su Ad Content (Contenuto annuncio). Utilizza il Titolo annuncio nel parametro utm_content . Se si tratta di un annuncio immagine, utilizza il titolo dell’annuncio e includi le dimensioni dell’annuncio.

Ad esempio, [titolo annuncio] 200x400px

**utm_term**: Viene mappato su Testo parole chiave. Usa questo parametro per indicare la parola chiave relativa all’attivazione dell’annuncio.

Se non è presente una parola chiave correlata all’annuncio, lascia vuoto questo parametro.

Ad esempio, iPhone App Ideas

**Lo tenga semplice e sintetico. Non duplicare sforzi, termini e canali.**

Immaginiamo la gerarchia dell&#39;UTM come segue:

Media > [!UICONTROL Source] > [!UICONTROL Campaign] > [!UICONTROL Content/Term]

Ad esempio, se un [!UICONTROL display] l’annuncio è posizionato su Facebook e si consiglia quanto segue:

fakewebsite.com/

?utm_medium=social

&amp;utm_source=facebook

&amp;utm_campaign=Display_campaign_ID

&amp;utm_content=content_of_campaign

Tieni presente che i termini/canale non sono duplicati e che in questo caso non viene utilizzato utm_term.

In caso di domande, contatta il team dell’account Adobe (il tuo Account Manager) o [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
