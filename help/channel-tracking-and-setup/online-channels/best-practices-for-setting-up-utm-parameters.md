---
unique-page-id: 18874732
description: Procedure consigliate per la configurazione dei parametri UTM - [!DNL Marketo Measure]
title: Procedure consigliate per la configurazione dei parametri UTM
exl-id: 56019f41-b6ba-48c1-9bef-2a5f56d2d5f4
feature: UTM Parameters
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Procedure consigliate per la configurazione dei parametri UTM {#best-practices-for-setting-up-utm-parameters}

I parametri UTM sono un ottimo modo per suddividere i dati di marketing. [!DNL Marketo Measure] utilizza e acquisisce tutti i parametri UTM per compilare i campi in Salesforce e nel [!DNL Marketo Measure] app. Grazie a queste informazioni, potrai comprendere in modo granulare da dove provengono i tuoi lead, opportunità e offerte chiuse/vinte.

È possibile utilizzare [Generatore URL di Google](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"} to set up your UTM parameters and add them to your links within your marketing efforts. Use this [Google Spreadsheet](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"} se desideri un modo più semplice per tenere traccia di tutti i collegamenti UTM.

## Valori di alto livello per ciascun parametro {#high-level-values-for-each-parameter}

**utm_medium**: questo campo viene mappato sul campo Medio. Utilizzare utm_medium per indicare il canale di alto livello.

Ad esempio: [!UICONTROL Social], CPC, e-mail, web, organico

Non utilizzare questo campo per richiamare il sottocanale.

**utm_source**: questo campo viene mappato sul campo Sorgente punto di contatto. Utilizzare utm_source per definire il sottocanale da cui ha origine il lead.

Ad esempio, Facebook, Twitter, Linkedin, Drip_email, Email_blast, newsletter.

Semplificala. Non utilizzare questo parametro per indicare i tipi di annunci, come retargeting o sponsorizzati. Non aggiungere utm_source = homepage, webdirect, sito Web. [!DNL Marketo Measure] compila automaticamente queste informazioni.

**utm_campaign**: questo campo è mappato sul nome della campagna pubblicitaria. Utilizza utm_campaign per indicare il titolo della campagna così come esiste nella piattaforma pubblicitaria o come viene indicato internamente.

Questo è anche un buon parametro per indicare la geolocalizzazione, il tipo di rete dell’annuncio (visualizzazione vs. ricerca) e così via.

Si consiglia di utilizzare i caratteri di sottolineatura anziché gli spazi ed evitare di utilizzare la punteggiatura. Questo riduce la possibilità di errori di codifica da parte dei browser durante la lettura dei parametri.

Ad esempio, AU_Idea_for_an_App_50k

**utm_content**: corrisponde al contenuto dell’annuncio. Utilizza Titolo annuncio nel parametro utm_content. Se si tratta di un annuncio di immagine, utilizza il titolo dell’annuncio e includi le dimensioni dell’annuncio.

Ad esempio: [titolo annuncio] 200x400px

**utm_term**: viene mappato al testo della parola chiave. Usa questo parametro per indicare la parola chiave relativa all’attivazione dell’annuncio.

Se non è presente alcuna parola chiave correlata all’annuncio, lascia vuoto questo parametro.

Ad esempio, Idee per app iPhone

**Semplificalo e sintetico. Non duplicare sforzi, termini e canali.**

Immaginiamo la gerarchia UTM come segue:

Media > [!UICONTROL Source] > [!UICONTROL Campaign] > [!UICONTROL Content/Term]

Ad esempio, se un [!UICONTROL display] L’annuncio viene inserito in Facebook. Si consiglia di effettuare le seguenti operazioni:

fakewebsite.com/

?utm_medium=social

&amp;utm_source=facebook

&amp;utm_campaign=Display_campaign_ID

&amp;utm_content=content_of_campaign

Tieni presente che i termini/canale non sono duplicati e che in questo caso utm_term non viene utilizzato.

In caso di domande, rivolgiti al team dell’account Adobe (il tuo Account Manager) oppure [Supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
