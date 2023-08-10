---
unique-page-id: 18874606
description: Parametri UTM - [!DNL Marketo Measure] - Documentazione del prodotto
title: Parametri UTM
exl-id: 2b20f3c4-1f39-4ac5-bad1-cb1d630d60e9
feature: UTM Parameters
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# Parametri UTM {#utm-parameters}

Assegnare tag agli URL è un modo semplice ed efficace per acquisire dati sulle attività di marketing digitale. Si tratta del processo di aggiunta di parametri alla fine degli URL che raccolgono e registrano dati. I parametri più comunemente utilizzati sono i moduli UTM (Urchin Tracking Modules), supportati da Google. Sono disponibili cinque parametri UTM principali: Medio, Origine, Campagna, Contenuto e Termine. Questi sono descritti più dettagliatamente nella sezione successiva.

I parametri UTM possono essere aggiunti manualmente agli URL o aggiunti tramite l’assegnazione tag automatica con determinate piattaforme, ad esempio AdWords. L’assegnazione automatica dei tag automatizza il processo di aggiunta dei parametri agli URL. È inoltre possibile: [Generatori di URL](https://ga-dev-tools.appspot.com/campaign-url-builder/){target="_blank"} per velocizzare l’assegnazione dei tag agli URL manualmente. Con un generatore di URL, devi semplicemente specificare i valori da utilizzare per ciascun parametro, e il generatore formatterà l’URL al tuo posto.

## Cosa sono i parametri UTM? {#what-are-utm-parameters}

Per comprendere il funzionamento dei parametri UTM, vediamo un URL tipico senza UTM:

`http://www.adobe.com`

Ora, estraiamo un URL con UTM:

`http://www.adobe.com?utm_medium=socialmedia&utm_source =facebook&utm_campaign=seasonal-sale&utm_content=photo-400x700px`

Come puoi vedere, il secondo collegamento contiene molto più testo. I parametri UTM seguono sempre il dominio di primo livello (.com in questo esempio) e iniziano con un punto interrogativo. In seguito, l’ordine dei parametri non ha importanza, ma si consiglia di seguire una convenzione di denominazione coerente. Le e commerciali devono essere posizionate tra ciascun parametro per separare ogni UTM. Ora possiamo andare più in dettaglio su ciò che ogni parametro rappresenta.

Informazioni su [best practice per la configurazione dei parametri UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md).

**utm_medium**

* Medium identifica i veicoli utilizzati per commercializzare l&#39;azienda.
* Risponde alla domanda: &quot;Come ti arrivano?&quot;
* Indica il canale di livello più alto.
* Social media, e-mail, ricerca organica e ricerca a pagamento sono tutti esempi di potenziali valori Medium.
* Questo parametro mappa i dati su [!DNL Marketo Measure] Campo &quot;Medio&quot;.
* _[!DNL Marketo Measure]Best practice:_ Non utilizzare questo campo per richiamare un sottocanale; in caso contrario, potrebbero verificarsi difficoltà nella generazione di rapporti sul canale effettivo. Utilizzalo per identificare il tuo veicolo di marketing o canale. Ad esempio, se desideri utilizzare l’e-mail per commercializzare il prodotto, il mezzo è l’e-mail.

**utm_source**

* Sorgente identifica il sottocanale che è la sorgente del traffico.
* Risponde alla domanda: &quot;Da dove viene questa persona?&quot;
* In un esempio di social media, la fonte del traffico è la piattaforma di social media utilizzata.
   * In questo esempio, [!DNL Facebook] è il valore sorgente. Altri esempi sono Twitter e Instagram. Se il supporto UTM è [!DNL Paid Search]Tuttavia, l’origine UTM potrebbe essere AdWords o BingAds.

* Questo parametro è mappato su [!DNL Marketo Measure] Campo &quot;Sorgente punto di contatto&quot; in SFDC.
* _[!DNL Marketo Measure]Best practice:_ Questo parametro tiene traccia dell’origine del traffico, pertanto non è appropriato utilizzarlo per indicare il tipo di annuncio, ad esempio retargeting, sponsorizzato, ecc. È meglio utilizzarlo per tenere traccia del sottocanale di livello superiore. Ricordate, state rispondendo alla domanda &quot;Da dove viene il mio traffico?&quot; Stai cercando il referente. In questo esempio, Origine UTM è il luogo in cui si trova l’annuncio (non la pagina web effettiva, in quanto viene tracciata automaticamente all’esterno dei tag). Se tieni traccia di una campagna e-mail goccia a goccia, la sorgente è la posta elettronica goccia a goccia.

**utm_campaign**

* La campagna viene utilizzata per identificare una campagna di marketing specifica.
* Risponde alla domanda: &quot;Perché vengono da te?&quot;
* Utilizza questo tag per indicare il nome della campagna pubblicitaria esistente in [!DNL Google AdWords] o [!DNL BingAds], o per indicare il nome con cui si identifica la campagna internamente. Puoi anche utilizzare questo tag per specificare altre informazioni, ad esempio la geolocalizzazione o il tipo di rete degli annunci.
* Questo parametro è mappato su [!DNL Marketo Measure] &#39;Campo Nome campagna annuncio&#39; in SFDC.
* _[!DNL Marketo Measure]Best practice_: quando determini i nomi delle campagne, evita di utilizzare segni di punteggiatura o spazi vuoti tra le parole, poiché il loro utilizzo può causare errori di codifica del browser. Per ottenere risultati ottimali, utilizza i caratteri di sottolineatura.

**utm_content**

* Utilizza il parametro Contenuto UTM quando vuoi tenere traccia di più elementi di marketing esistenti in una singola pagina web. Ad esempio, se disponi di un pulsante &quot;Richiedi una demo&quot; e di un pulsante &quot;Registrati alla nostra newsletter settimanale&quot; e desideri sapere quale genera più traffico, puoi denominare ciascuno di essi e utilizzare un tag di contenuto UTM per tracciarli. Il nome di ogni elemento di &quot;contenuto&quot; è il valore del tag.
* Questo parametro è mappato su [!DNL Marketo Measure] Campo &quot;Contenuto annuncio&quot; in SFDC.
* _[!DNL Marketo Measure]Best practice_: valore facoltativo, ma [!DNL Marketo Measure] consiglia di utilizzarlo. Questo tag è associato al titolo dell’annuncio o del pezzo di marketing che desideri tracciare. Se utilizzi un annuncio di immagine, assicurati di scriverne le dimensioni nel titolo.

**utm_term**

* Il termine è simile al parametro del contenuto UTM. Il termine è ideale per identificare le parole chiave negli annunci per le campagne a pagamento. Se utilizzi la funzione di assegnazione automatica tag, questa operazione viene eseguita automaticamente. Se non utilizzi la funzione di assegnazione automatica tag della piattaforma di annunci, assicurati di aggiungere con attenzione tutte le parole chiave di cui desideri tenere traccia.
* Questo parametro è mappato su [!DNL Marketo Measure] Campo &#39;Testo parola chiave&#39; in SFDC.
* _[!DNL Marketo Measure]Best practice_: il tag Termine UTM è facoltativo, ma ottimo per il tracciamento delle parole chiave. Eseguire un doppio controllo ortografico ed evitare di utilizzare caratteri speciali. Se sono necessarie più parole, prova a usare il carattere di sottolineatura o a non usare spazi.

Ogni parametro raccoglie informazioni rilevanti per il valore assegnato. Il valore di ogni tag ti consente di tracciare e ordinare tutte le campagne digitali e rispondere alle seguenti domande: dove, come e perché?

Ecco un grafico dei parametri UTM [!DNL Marketo Measure] analizza e il campo corrispondente del punto di contatto a cui sono associati:

| **Parametro UTM** | **Corrispondente [!DNL Marketo Measure] Campo** |
|---|---|
| utm_medium | Medium |
| utm_source | Sorgente punto di contatto |
| utm_campaign | Nome campagna pubblicitaria |
| utm_content | Contenuto annuncio |
| utm_term | Testo parola chiave |
