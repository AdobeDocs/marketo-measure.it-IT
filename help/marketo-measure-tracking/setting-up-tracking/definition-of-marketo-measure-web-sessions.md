---
unique-page-id: 18874564
description: Definizione di [!DNL Marketo Measure] Sessioni web - [!DNL Marketo Measure] - Documentazione del prodotto
title: Definizione di [!DNL Marketo Measure] Sessioni web
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Definizione di [!DNL Marketo Measure] Sessioni web {#definition-of-marketo-measure-web-sessions}

Scopri come [!DNL Marketo Measure] definisce le sessioni web.

A **sessione web** si riferisce alle interazioni di un individuo con il sito web durante un certo periodo di tempo. La sessione inizia quando un utente arriva al tuo sito web.

Ad esempio, Haley visita adobe.com. La sua visita al sito inizia una sessione. Quando Haley lascia il sito, chiudendo la scheda/browser Web o uscendo dal sito, la sessione termina.

Un utente non può aprire più sessioni contemporaneamente. Se Haley apre [!DNL adobe.com] in 10 schede separate, è stata creata una sola sessione in relazione alla sua visita al sito web.

## In che modo [!DNL Marketo Measure] definire una nuova sessione? {#how-does-marketo-measure-define-a-new-session}

Esistono alcuni fattori che determinano la fine di una sessione e l’inizio di una nuova sessione. I due modi principali [!DNL Marketo Measure] Le sessioni possono terminare nelle seguenti situazioni:

* **Scadenza basata sul tempo**
* **Scadenza basata su canale**

## Scadenza basata su tempo {#time-based-expiration}

**Quanto dura una sessione?**

[!DNL Marketo Measure] Le sessioni termineranno dopo 30 minuti di inattività sul sito web. Ad esempio:

Quando Haley visita adobe.com, inizia una sessione. Esplora il sito web per qualche minuto e poi si allontana dal computer, ma lascia il sito aperto. Dopo 30 minuti di inattività la sessione terminerà.

Attualmente, [!DNL Marketo Measure] considera solo la navigazione nelle pagine e l’invio di moduli come attività. Lo scorrimento della pagina web o il passaggio del mouse su un elemento della pagina non sono considerati attività. Quindi se Haley visita adobe.com per leggere un post di blog, e le ci vuole un&#39;ora per leggere, la sua sessione web terminerà dopo 30 minuti anche se sta scorrendo il contenuto della pagina.

## Scadenza basata sul canale {#channel-based-expiration}

[!DNL Marketo Measure] inizierà una nuova sessione ogni volta che un utente accede al tuo sito web da un canale di marketing digitale diverso o da un sito web esterno. Ciò include:

* Un sito Web di riferimento
* Canali social ([!DNL Facebook], [!DNL LinkedIn], ecc.)
* Canali di ricerca a pagamento o organica ([!DNL Google/Bing])

**Siti Web di riferimento e canali social**

Ogni volta che un visitatore accede al tuo sito web da un sito web di riferimento o da un canale di social network, inizia una nuova sessione.

Dire che Haley è su LinkedIn, clicca su [!DNL Marketo Measure] e viene reindirizzato al sito web dell’Adobe. Quindi, durante lo scorrimento [!DNL Facebook], Haley vede un&#39;altra [!DNL Marketo Measure] post. Quando fa clic su questo post e viene reindirizzata al sito di Adobe, si verifica la prima sessione Web correlata a [!DNL LinkedIn] e una nuova sessione correlata a [!DNL Facebook] inizia.

**Canali di ricerca a pagamento o organica**

Le nuove sessioni inizieranno ogni volta che un utente accede al sito tramite canali di ricerca organici o a pagamento. Se Haley accede al sito web dell’Adobe tramite ricerca organica e poi visita immediatamente il sito web tramite un annuncio a pagamento su Google, verranno create due sessioni separate.

**Traffico diretto web**

Se un visitatore accede al tuo sito web digitando l’URL del sito web nella barra degli indirizzi, non sempre inizia una nuova sessione.

Se la prima sessione web di Haley inizia come risultato di una visita da un sito di riferimento, un canale di social network o un canale di ricerca a pagamento/organico e poi visita il sito tramite web direct, questo non causerebbe l’inizio di una nuova sessione.

_Tuttavia_, se la prima sessione web di Haley ha avuto origine da Web Direct e poi visita il sito tramite _un sito esterno/di riferimento_, la prima sessione termina e viene aperta una nuova sessione correlata al sito esterno/di riferimento.

## Google Analytics sessioni {#google-analytics-sessions}

Ci sono alcune somiglianze con [!DNL Marketo Measure] e Google Analytics definisce le sessioni. Per ulteriori informazioni su come Google Analytics definisce le sessioni, visita: [https://support.google.com/analytics/answer/2731565?hl=en](http://support.google.com/analytics/answer/2731565?hl=en){target="_blank"}
