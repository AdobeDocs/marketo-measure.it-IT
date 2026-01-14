---
description: Spiegazione di [!DNL Marketo Measure] approfondimenti - [!DNL Marketo Measure]
title: Spiegazione di [!DNL Marketo Measure] approfondimenti
exl-id: d479a15f-4c92-4302-8ce8-6487645012e1
feature: Reporting
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Spiegazione di [!DNL Marketo Measure] approfondimenti {#marketo-measure-insights-explained}

Scopri la visualizzazione Approfondimenti di [!DNL Marketo Measure] in [!DNL Salesforce], compresi gli elementi rappresentati dalle diverse icone e come utilizzare la funzione. Questa funzione è particolarmente utile per visualizzare le prime 20 sessioni di un lead, contatto o account.

Una volta che un utente viene monitorato dal JavaScript [!DNL Marketo Measure] e compila un modulo sul sito Web, diventa un lead nel sistema e i suoi dati di marketing digitale vengono inviati all&#39;organizzazione Salesforce (SFDC). In questo caso, vengono visualizzati i dati del punto di contatto popolati nella sezione [!DNL Marketo Measure] Informazioni lead (un&#39;app Canvas) sugli oggetti lead/contatto/opportunità/account.

Innanzitutto, nella parte centrale delle tue informazioni, vedi il numero di sessioni che la persona ha avuto sul tuo sito web. Puoi scorrere queste sessioni e navigare a tuo piacimento.

![Nella parte centrale delle informazioni viene visualizzato il numero](assets/marketo-app-1.png)

Puoi esaminare il rollup di tutte le sessioni facendo clic su &quot;Tutto&quot; nella parte medio-superiore delle tue informazioni. Qui puoi comprendere le date delle singole sessioni, il canale o la sorgente che le ha guidate e una serie di icone che specificano ulteriori informazioni.

La prima cosa che vedete sono le icone FT o LC. Questi rappresentano la posizione del punto di contatto delle sessioni elencate. Nello specifico, FT sta per First Touch e LC sta per Lead Creation. Puoi avere più sessioni, ma solo un punto di contatto può essere il FT o LC. Non troverai mai più FT o LC associati a una persona.

Le icone che sembrano fogli indicano che si è verificata una visualizzazione di pagina durante la sessione. È probabile che ogni sessione includa questa icona.

![Le icone che sembrano carta indicano che è avvenuta una visualizzazione di pagina](assets/marketo-app-2.png)

L’icona che sembra un becher segnala che si è verificato un esperimento di test A/B. A questo punto ci integriamo con Optimizely e VWO. Con questa integrazione, siamo in grado di inviare in push l’esperimento e la variante che l’utente ha visto nella sua sessione specifica.

![L&#39;icona che sembra un becher segnala che un test A/B](assets/marketo-app-3.png)

Se fai clic su una sessione specifica (per farlo, fai clic sulla data effettiva della sessione o nella parte superiore centrale delle sessioni raggruppate), potrai visualizzare i dettagli della sessione. In ogni sessione, puoi visualizzare tutte le pagine specifiche che l’utente ha visto ordinate per data e ora.

![Se fai clic su una sessione specifica (per farlo, fai clic su](assets/marketo-app-4.png))

Sul lato destro di ogni sessione puoi vedere più dati di marketing granulari che stanno spingendo i campi [!DNL Marketo Measure] nel tuo SFDC. In questo esempio, puoi visualizzare Gruppo di annunci, Contenuto annuncio, Campagna, Parola chiave, Medium. È inoltre possibile scorrere verso il basso per visualizzare ulteriori dati di [!DNL Marketo Measure] forniti.

Infine, una volta che qualcuno ha una miriade di sessioni, puoi utilizzare alcuni filtri in [!UICONTROL Insights] per cercare parti specifiche del suo coinvolgimento sul tuo sito. È possibile filtrare per [!UICONTROL Touchpoint Position], ad esempio.

È inoltre possibile eseguire ricerche per visualizzazioni di pagina, test AB o Forms.
