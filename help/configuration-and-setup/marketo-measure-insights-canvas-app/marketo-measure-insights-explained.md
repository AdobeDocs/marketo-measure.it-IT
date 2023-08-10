---
unique-page-id: 18874676
description: "[!DNL Marketo Measure] Spiegazione approfondimenti - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Spiegazione approfondimenti"
exl-id: d479a15f-4c92-4302-8ce8-6487645012e1
feature: Reporting
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# [!DNL Marketo Measure] Spiegazione approfondimenti {#marketo-measure-insights-explained}

Scopri di più su [!DNL Marketo Measure] Visualizzazione approfondimenti in [!DNL Salesforce], tra cui cosa rappresentano le diverse icone e come utilizzare la funzione. Questa funzione è particolarmente utile per visualizzare le prime 20 sessioni di un lead, contatto o account.

Quando qualcuno viene tracciato da [!DNL Marketo Measure] JavaScript e compila un modulo sul sito web, la persona diventerà un lead nel sistema e i dati di marketing digitale verranno inviati all’organizzazione Salesforce (SFDC). In questo caso, vedrai i dati del punto di contatto popolati all&#39;interno del [!DNL Marketo Measure] Sezione Informazioni lead (un’app Canvas) sugli oggetti Lead/Contact/Opportunity/Account.

Per prima cosa, nella parte centrale delle tue informazioni vedrai il numero di sessioni che la persona ha avuto sul tuo sito web. Puoi scorrere queste sessioni e navigare a tuo piacimento.

![](assets/1.png)

Puoi esaminare il rollup di tutte le sessioni facendo clic su &quot;Tutto&quot; nella parte medio-superiore delle tue informazioni. Qui potrai comprendere le date delle singole sessioni, quale canale o sorgente li ha guidati e una serie di icone che specificano ulteriori informazioni.

La prima cosa che vedrete sono le icone FT o LC. Questi rappresentano la posizione del punto di contatto delle sessioni elencate. Nello specifico, FT sta per First Touch e LC sta per Lead Creation. Puoi avere più sessioni, ma solo un punto di contatto può essere il FT o LC. Non troverai mai più FT o LC associati a una persona.

Le icone che sembrano fogli indicano che si è verificata una visualizzazione di pagina durante la sessione. È probabile che ogni sessione includa questa icona.

![](assets/2.png)

L’icona che sembra un becher segnala che si è verificato un esperimento di test A/B. A questo punto ci integriamo con Optimizely e VWO. Con questa integrazione, siamo in grado di inviare in push l’esperimento e la variante che l’utente ha visto nella sua sessione specifica.

![](assets/3.png)

Se fai clic su una sessione specifica (per farlo, fai clic sulla data effettiva della sessione o nella parte superiore centrale delle sessioni raggruppate), potrai vedere i dettagli della sessione. In ogni sessione, puoi visualizzare tutte le pagine specifiche che l’utente ha visto ordinate per data e ora.

![](assets/4.png)

Sul lato destro di ogni sessione puoi vedere una quantità maggiore dei dati di marketing granulari che inviamo al [!DNL Marketo Measure] campi nell’SFDC. In questo esempio, puoi visualizzare Gruppo di annunci, Contenuto annuncio, Campagna, Parola chiave, Medio. Puoi anche scorrere verso il basso per visualizzare più di [!DNL Marketo Measure] i dati che forniamo.

Infine, una volta che qualcuno ha una miriade di sessioni, puoi utilizzare alcuni filtri in [!UICONTROL Insights] per cercare parti specifiche del loro coinvolgimento sul sito. Puoi filtrare per [!UICONTROL Touchpoint Position] ad esempio.

È inoltre possibile eseguire ricerche per visualizzazioni di pagina, test AB o Forms.
