---
description: Procedure consigliate per la configurazione dei parametri UTM - Linee guida per gli utenti di Marketo Measure
title: Procedure consigliate per la configurazione dei parametri UTM
exl-id: 56019f41-b6ba-48c1-9bef-2a5f56d2d5f4
feature: UTM Parameters
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Procedure consigliate per la configurazione dei parametri UTM {#best-practices-for-setting-up-utm-parameters}

I parametri UTM sono un ottimo modo per suddividere i dati di marketing. [!DNL Marketo Measure] utilizza e acquisisce tutti i parametri UTM per compilare i campi in Salesforce e nell&#39;app [!DNL Marketo Measure]. Grazie a queste informazioni, potrai comprendere in modo granulare da dove provengono i tuoi lead, opportunità e offerte chiuse/vinte.

Puoi utilizzare [Google URL Builder](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"} per impostare i parametri UTM e aggiungerli ai collegamenti all&#39;interno delle tue attività di marketing. Utilizza questo [foglio di calcolo Google](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"} se desideri un modo più semplice per tenere traccia di tutti i collegamenti UTM.

## Valori di alto livello per ciascun parametro {#high-level-values-for-each-parameter}

**utm_medium**: questo campo viene mappato al campo Medium. Utilizzare utm_medium per indicare il canale di alto livello.

Ad esempio, [!UICONTROL Social], CPC, e-mail, web, organico

Non utilizzare questo campo per richiamare il sottocanale.

**utm_source**: questo campo viene mappato al campo Source del punto di contatto. Utilizzare utm_source per definire il sottocanale da cui ha origine il lead.

Ad esempio, Facebook, Twitter, LinkedIn, Drip_email, Email_blast, newsletter.

Semplificala. Non utilizzare questo parametro per indicare i tipi di annunci, come retargeting o sponsorizzati. Non aggiungere utm_source = homepage, webdirect, sito Web. [!DNL Marketo Measure] compila automaticamente queste informazioni.

**utm_campaign**: questo campo è mappato al nome della campagna pubblicitaria. Utilizza utm_campaign per indicare il titolo della campagna così come esiste nella piattaforma pubblicitaria o come viene indicato internamente.

Questo è anche un buon parametro per indicare la geolocalizzazione, il tipo di rete dell’annuncio (visualizzazione vs. ricerca) e così via.

Si consiglia di utilizzare i caratteri di sottolineatura anziché gli spazi ed evitare di utilizzare la punteggiatura. Questo riduce la possibilità di errori di codifica da parte dei browser durante la lettura dei parametri.

Ad esempio, AU_Idea_for_an_App_50k

**utm_content**: mappato al contenuto dell&#39;annuncio. Utilizza Titolo annuncio nel parametro utm_content. Se si tratta di un annuncio di immagine, utilizza il titolo dell’annuncio e includi le dimensioni dell’annuncio.

Ad esempio, [titolo annuncio] 200x400px

**utm_term**: corrisponde al testo della parola chiave. Usa questo parametro per indicare la parola chiave relativa all’attivazione dell’annuncio.

Se non è presente alcuna parola chiave correlata all’annuncio, lascia vuoto questo parametro.

Ad esempio, Idee per app iPhone

**Semplifica e riepiloga. Non duplicare sforzi, termini e canali.**

Immaginiamo la gerarchia UTM come segue:

Medium > [!UICONTROL Source] > [!UICONTROL Campaign] > [!UICONTROL Content/Term]

Ad esempio, se un annuncio [!UICONTROL display] viene inserito su Facebook, si consiglia quanto segue:

`fakewebsite.com/?utm_medium=social&utm_source=facebook&utm_campaign=Display_campaign_ID&utm_content=content_of_campaign`

Tieni presente che i termini/canale non sono duplicati e che in questo caso utm_term non viene utilizzato.

In caso di domande, contatta il team dell&#39;account Adobe (il tuo Account Manager) o il [supporto Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
