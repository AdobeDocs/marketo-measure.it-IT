---
unique-page-id: 18874564
description: Definizione di  [!DNL Marketo Measure] sessioni Web - [!DNL Marketo Measure]
title: Definizione di  [!DNL Marketo Measure] sessioni Web
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Definizione di [!DNL Marketo Measure] sessioni Web {#definition-of-marketo-measure-web-sessions}

Scopri come [!DNL Marketo Measure] definisce le sessioni web.

Una **sessione Web** fa riferimento alle interazioni di un individuo con il sito Web durante un certo periodo di tempo. La sessione inizia quando un utente arriva al tuo sito web.

Ad esempio, Haley visita adobe.com. La sua visita al sito inizia una sessione. Quando Haley lascia il sito, chiudendo la scheda/browser Web o uscendo dal sito, la sessione termina.

Un utente non può aprire più sessioni contemporaneamente. Se Haley apre [!DNL adobe.com] in dieci schede separate, è stata creata una sola sessione in relazione alla sua visita al sito Web.

## Come definisce [!DNL Marketo Measure] una nuova sessione? {#how-does-marketo-measure-define-a-new-session}

Esistono alcuni fattori che determinano la fine di una sessione e l’inizio di una nuova sessione. I due modi principali in cui [!DNL Marketo Measure] sessioni possono terminare sono:

* **Scadenza basata sul tempo**
* **Scadenza basata sul canale**

## Scadenza basata su tempo {#time-based-expiration}

**Quanto dura una sessione?**

[!DNL Marketo Measure] sessioni termineranno dopo 30 minuti di inattività sul sito Web. Ad esempio:

Quando Haley visita adobe.com, inizia una sessione. Esplora il sito web per qualche minuto e poi si allontana dal computer, ma lascia il sito aperto. La sessione termina dopo 30 minuti di inattività.

Attualmente, [!DNL Marketo Measure] considera solo l&#39;esplorazione delle pagine e l&#39;invio di moduli come attività. Lo scorrimento della pagina web o il passaggio del mouse su un elemento della pagina non sono considerati attività. Quindi se Haley visita adobe.com per leggere un post di blog, e le ci vuole un&#39;ora per leggere, la sua sessione web terminerà dopo 30 minuti anche se sta scorrendo il contenuto della pagina.

## Scadenza basata sul canale {#channel-based-expiration}

[!DNL Marketo Measure] inizia una nuova sessione ogni volta che un utente accede al tuo sito Web da un canale di marketing digitale diverso o da un sito Web esterno. Ciò include:

* Un sito Web di riferimento
* Canali social ([!DNL Facebook], [!DNL LinkedIn] e così via)
* Canali di ricerca a pagamento o organica ([!DNL Google/Bing])

**Siti Web di riferimento e canali social**

Ogni volta che un visitatore accede al tuo sito web da un sito web di riferimento o da un canale social, inizia una nuova sessione.

Supponiamo che Haley sia su LinkedIn, faccia clic su un post di [!DNL Marketo Measure] e venga reindirizzato al sito Web dell&#39;Adobe. Quindi, durante lo scorrimento di [!DNL Facebook], Haley visualizza un altro post di [!DNL Marketo Measure]. Quando fa clic su questo post e viene reindirizzata al sito di Adobe, la prima sessione Web correlata a [!DNL LinkedIn] viene terminata e inizia una nuova sessione correlata a [!DNL Facebook].

**Canali di ricerca a pagamento o organica**

Le nuove sessioni iniziano ogni volta che un utente accede al sito tramite canali di ricerca organici o a pagamento. Se Haley accede al sito web dell’Adobe tramite ricerca organica e poi visita immediatamente il sito web tramite un annuncio a pagamento su Google, vengono create due sessioni separate.

**Traffico diretto Web**

Se un visitatore accede al tuo sito web digitando l’URL del sito web nella barra degli indirizzi, non sempre inizia una nuova sessione.

Se la prima sessione web di Haley inizia come risultato di una visita da un sito di riferimento, un canale di social network o un canale di ricerca a pagamento/organico e poi visita il sito tramite web direct, questo non causerebbe l’inizio di una nuova sessione.

_Tuttavia_, se la prima sessione Web di Haley ha avuto origine da Web Direct e successivamente visita il sito Web tramite _un sito esterno/di riferimento_, la prima sessione termina e viene aperta una nuova sessione relativa al sito esterno/di riferimento.

## Google Analytics sessioni {#google-analytics-sessions}

Ci sono alcune somiglianze con il modo in cui [!DNL Marketo Measure] e Google Analytics definiscono le sessioni. Per ulteriori informazioni su come Google Analytics definisce le sessioni, visitare: [https://support.google.com/analytics/answer/2731565?hl=en](https://support.google.com/analytics/answer/2731565?hl=en){target="_blank"}
