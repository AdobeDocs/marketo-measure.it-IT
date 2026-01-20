---
unique-page-id: 18874564
description: Definizione di  [!DNL Marketo Measure] sessioni Web - [!DNL Marketo Measure]
title: Definizione di  [!DNL Marketo Measure] sessioni Web
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '807'
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

### Comportamento legacy {#legacy-behavior}

**Quanto dura una sessione?**

[!UICONTROL Marketo Measure] sessioni termineranno dopo 30 minuti di inattività sul sito Web. Ad esempio:

Quando Haley visita adobe.com, inizia una sessione. Esplora il sito web per qualche minuto e poi si allontana dal computer, ma lascia il sito aperto. La sessione termina dopo 30 minuti di inattività.

Attualmente, [!UICONTROL Marketo Measure] considera solo l&#39;esplorazione delle pagine e l&#39;invio di moduli come attività. Lo scorrimento della pagina web o il passaggio del mouse su un elemento della pagina non sono considerati attività. Quindi se Haley visita adobe.com per leggere un post di blog, e le ci vuole un&#39;ora per leggere, la sua sessione web terminerà dopo 30 minuti anche se sta scorrendo il contenuto della pagina.

### Nuovo comportamento {#new-behavior}

Per i nuovi utenti, questo sarà il comportamento predefinito.

Gli utenti esistenti possono adottare il nuovo comportamento attivando l&#39;interruttore in **Impostazioni** > **Attribuzione Everytouch** > **Riporto canale sessione**. Una volta attivata, questa impostazione non può essere annullata.

Quando viene creata una nuova sessione dopo 30 minuti di inattività, il canale della sessione precedente viene trasferito se la nuova sessione inizia entro sette giorni. Questo riporto si applica solo alle visite dirette (senza referrer o referrer interni). Se l’inattività supera i sette giorni, per impostazione predefinita il canale della nuova sessione è Diretto/Altro. Ad esempio, se Haley visita landingpage.com da Google, è inattiva per oltre 30 minuti e ritorna entro sette giorni, la nuova sessione manterrà il canale Google. Tuttavia, se lo stesso utente rivede la pagina tramite un canale diverso, il canale non diretto non viene sovrascritto dal canale Google precedente.

Solo il canale verrà trasferito, esclusi i dettagli della campagna o del referente. Questo perché la classificazione del canale è gestita da Marketo Measure, mentre gli altri punti dati vengono raccolti separatamente.

**Accesso social**

Quando un visitatore utilizza l’accesso tramite social network tramite Google, Microsoft o Apple, la sessione viene unita in un’unica sessione continua. Ad esempio, se un visitatore arriva a una pagina da LinkedIn, completa un accesso social Google e raggiunge una pagina di ringraziamento, verranno conteggiati tutti come una singola sessione. Senza l’attivazione del riporto del canale di sessione, l’accesso social creerebbe sessioni separate a causa del referente esterno.

## Scadenza basata sul canale {#channel-based-expiration}

[!DNL Marketo Measure] inizia una nuova sessione ogni volta che un utente accede al tuo sito Web da un canale di marketing digitale diverso o da un sito Web esterno. Ciò include:

* Un sito Web di riferimento
* Canali social ([!DNL Facebook], [!DNL LinkedIn] e così via)
* Canali di ricerca a pagamento o organica ([!DNL Google/Bing])

**Siti Web di riferimento e canali social**

Ogni volta che un visitatore accede al tuo sito web da un sito web di riferimento o da un canale social, inizia una nuova sessione.

Supponiamo che Haley sia su LinkedIn, faccia clic su un post [!DNL Marketo Measure] e venga reindirizzato al sito Web Adobe. Quindi, durante lo scorrimento di [!DNL Facebook], Haley visualizza un altro post di [!DNL Marketo Measure]. Quando fa clic su questo post e viene reindirizzata al sito Adobe, la prima sessione Web correlata a [!DNL LinkedIn] viene terminata e inizia una nuova sessione correlata a [!DNL Facebook].

**Canali di ricerca a pagamento o organica**

Le nuove sessioni iniziano ogni volta che un utente accede al sito tramite canali di ricerca organici o a pagamento. Se Haley accede al sito web di Adobe tramite ricerca organica e poi visita immediatamente il sito web tramite un annuncio a pagamento su Google, vengono create due sessioni separate.

**Traffico diretto Web**

Se un visitatore accede al tuo sito web digitando l’URL del sito web nella barra degli indirizzi, non sempre inizia una nuova sessione.

Se la prima sessione web di Haley inizia come risultato di una visita da un sito di riferimento, un canale di social network o un canale di ricerca a pagamento/organico e poi visita il sito tramite web direct, questo non causerebbe l’inizio di una nuova sessione.

_Tuttavia_, se la prima sessione Web di Haley ha avuto origine da Web Direct e successivamente visita il sito Web tramite _un sito esterno/di riferimento_, la prima sessione termina e viene aperta una nuova sessione relativa al sito esterno/di riferimento.

## Sessioni Google Analytics {#google-analytics-sessions}

Ci sono alcune somiglianze con il modo in cui [!DNL Marketo Measure] e Google Analytics definiscono le sessioni. Per ulteriori informazioni sulla definizione delle sessioni da parte di Google Analytics, visitare: [https://support.google.com/analytics/answer/2731565?hl=en](https://support.google.com/analytics/answer/2731565?hl=en){target="_blank"}
