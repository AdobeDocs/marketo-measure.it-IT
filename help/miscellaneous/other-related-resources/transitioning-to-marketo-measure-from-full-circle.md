---
unique-page-id: 18874535
description: Transizione verso [!DNL Marketo Measure] da Full Circle - [!DNL Marketo Measure] - Documentazione del prodotto
title: Transizione verso [!DNL Marketo Measure] da Full Circle
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Transizione verso [!DNL Marketo Measure] da Full Circle {#transitioning-to-marketo-measure-from-full-circle}

Passaggio da Full Circle a [!DNL Marketo Measure]? Lei non è da solo. Ecco le considerazioni più importanti da tenere a mente e le lezioni che abbiamo imparato da altri clienti che hanno fatto il passaggio.

## Tracciamento basato su campagne e tracciamento basato su più sorgenti {#campaign-based-tracking-vs-multi-source-tracking}

Tutte le interazioni in [!UICONTROL Full Circle] sono monitorate tramite l&#39;iscrizione alla campagna CRM. Con [!DNL Marketo Measure], il percorso di acquisto è compilato tramite una combinazione dei nostri record di attività JavaScript, di appartenenza alla campagna CRM e CRM. Per far sì che il nostro reporting di attribuzione funzioni, è necessario tenere traccia del passaggio mentale da &quot;tutte le interazioni devono essere tracciate in una campagna CRM affinché il nostro reporting di attribuzione funzioni&quot; a &quot;solo questo sottoinsieme di interazioni deve essere tracciato in una campagna CRM per il funzionamento del rapporto di attribuzione&quot; può essere complicato.

In generale, ecco come [!DNL Marketo Measure] crea record dei punti di contatto per i principali tipi di interazioni:

* Compilazione di moduli sui siti: [!DNL Marketo Measure] Javascript
* Visualizzazioni di pagina sui siti: Creato da [!DNL Marketo Measure] Javascript solo se questa visualizzazione di pagina ha generato una pietra miliare CRM designata (come la creazione di lead o opportunità)
* Interazioni offline come conferenze o fiere: iscrizione alla campagna CRM
* Interazioni digitali che avvengono ovunque su Internet e non sul tuo sito (ad esempio un webinar ospitato su un sito di terze parti che genera un caricamento di elenchi): iscrizione alla campagna CRM
* Interazioni con il team di vendita: Record di attività CRM

Se ti senti a tuo agio con la gestione della campagna CRM e preferisci mantenere in vigore i processi esistenti, va bene. Non fa male [!DNL Marketo Measure] per continuare a tenere traccia di tutte le interazioni nelle campagne CRM. Puoi progettare logica che crea solo punti di contatto da un sottoinsieme desiderato di campagne per evitare la duplicazione di punti di contatto.

## Visibilità e attribuzione {#visibility-vs-attribution}

Con la maggior parte delle configurazioni Full Circle puoi vedere ogni singola interazione di una persona con le tue attività di marketing o di vendita. Visualizzazioni di pagina, visite di pagina ripetute, iscrizione a campagne duplicate e triplicate: Full Circle ne sovrappone tutte. Se visualizzi una pagina 300 volte, Full Circle crea 300 campagne duplicate e ti fornisce un&#39;iscrizione a ognuna di esse. [!DNL Marketo Measure] no, e questa è stata una decisione consapevole del design da parte nostra.

[!DNL Marketo Measure] mira a fornire un brano di attribuzione che riproduce in modo appropriato interazioni significative e distribuisce in modo appropriato il peso tra i punti di contatto più importanti. Ad esempio, il [!DNL Marketo Measure] il framework non presenta le visualizzazioni di pagina (senza riempimenti di moduli) come punti di contatto di routine. È probabile che una visualizzazione di pagina autonoma non abbia un impatto sull’avanzamento di un percorso di acquisto, ma creeremo un punto di contatto se si tratta dell’interazione più recente prima di un cardine di gestione delle relazioni con i clienti designato (ad esempio, Creazione di lead o opportunità). Non vogliamo mostrarti tutto. Vogliamo mostrarti le cose che contano, dal punto di vista dell’attribuzione.

Lavora con il tuo [!DNL Marketo Measure] per impostare le aspettative appropriate sui dati che non saranno più disponibili per il team.

## Pre-[!DNL Marketo Measure] Dati {#pre-marketo-measure-data}

La raccomandazione standard consiste nell’avviare la generazione di rapporti e la raccolta di dati dal giorno in cui hai implementato la [!DNL Marketo Measure] JavaScript in avanti, e questo va doppio per i clienti precedenti di Full Circle. Pensate alle due sezioni precedenti: Sei abituato a vedere una maggiore quantità di dati, e sei abituato a tutti quei dati provenienti dall&#39;appartenenza alla campagna CRM. Se scegli di includere parte o tutti i dati da prima del tuo [!DNL Marketo Measure] implementazione, non effettuerai confronti tra le mele e le mele nella data di implementazione di JavaScript.

Detto questo, comprendiamo certamente che molti clienti hanno bisogno di questi dati storici; specialmente se si dispone di un ciclo di vendita più lungo (superiore a 90 giorni), si può voler dare [!DNL Marketo Measure] visibilità[!DNL Marketo Measure] dati. Discuti attentamente con il tuo [!DNL Marketo Measure] Tieni presente che l’alterazione della data di implementazione può comportare miglioramenti o diminuzioni delle prestazioni o del coinvolgimento del canale, nonché altre inferenze potenzialmente errate.

## In Riepilogo {#in-summary}

Sei in buona compagnia e abbiamo aiutato molti altri clienti a gestire questi cambiamenti. Lavora con il tuo [!DNL Marketo Measure] per capire gli impatti di cui sopra, così come qualsiasi altro problema che potresti avere.
