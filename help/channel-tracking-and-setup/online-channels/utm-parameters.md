---
unique-page-id: 18874606
description: Parametri UTM - [!DNL Marketo Measure] - Documentazione del prodotto
title: Parametri UTM
exl-id: 2b20f3c4-1f39-4ac5-bad1-cb1d630d60e9
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---

# Parametri UTM {#utm-parameters}

L’assegnazione tag agli URL è un modo semplice ed efficace per acquisire dati sulle attività di marketing digitale. È il processo di aggiunta di parametri alla fine degli URL che raccolgono e registrano i dati. I parametri più comunemente utilizzati sono i moduli di monitoraggio di Urchin (UTM), supportati da Google. Sono disponibili cinque parametri principali di UTM: Media, Origine, Campagna, Contenuto e Termine. Questi sono descritti più dettagliatamente nella sezione successiva.

I parametri UTM possono essere aggiunti manualmente agli URL o aggiunti tramite l’assegnazione tag automatica a determinate piattaforme, ad esempio AdWords. L’assegnazione tag automatica automatizza il processo di aggiunta di parametri agli URL. C&#39;è anche la possibilità di [Generatori di URL](https://ga-dev-tools.appspot.com/campaign-url-builder/){target=&quot;_blank&quot;} per velocizzare manualmente gli URL di assegnazione tag. Con un generatore di URL, devi solo specificare i valori da utilizzare per ogni parametro e il generatore formatta l’URL per te.

## Cosa sono i parametri UTM? {#what-are-utm-parameters}

Per comprendere come funzionano i parametri UTM, osserviamo un URL tipico senza UTM:

`http://www.adobe.com`

Ora, estraiamo un URL con gli UTM:

`http://www.adobe.com?utm_medium=socialmedia&utm_source =facebook&utm_campaign=seasonal-sale&utm_content=photo-400x700px`

Come puoi vedere, il secondo collegamento contiene molto più testo. I parametri UTM seguono sempre il dominio di primo livello (.com in questo esempio) e iniziano con un punto interrogativo. In seguito, l’ordine dei parametri non ha importanza, ma è consigliabile seguire una convenzione di denominazione coerente. Le e commerciali devono essere posizionate tra ciascun parametro per separare ciascun UTM. Ora possiamo andare più nel dettaglio di ciò che ogni parametro rappresenta.

Scopri [best practice per l’impostazione dei parametri UTM](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md).

**utm_medium**

* Il supporto identifica i veicoli utilizzati per commercializzare l&#39;azienda.
* Risponde alla domanda: &quot;Come ti arrivano?&quot;
* Indica il canale di livello più alto.
* I social media, le e-mail, la ricerca organica e la ricerca a pagamento sono tutti esempi di potenziali valori medi.
* Questo parametro mappa i dati al [!DNL Marketo Measure] Campo &#39;Medium&#39;.
* _[!DNL Marketo Measure]Best practice:_ Non utilizzare questo campo per richiamare un canale secondario, altrimenti potrebbero verificarsi difficoltà nella generazione di rapporti sul canale effettivo. Utilizzalo per identificare il tuo veicolo o canale di marketing. Ad esempio, se desideri utilizzare l’e-mail per commercializzare il prodotto, il supporto è e-mail.

**utm_source**

* Origine identifica il canale secondario che è l&#39;origine del traffico.
* Risponde alla domanda: &quot;Da dove viene questa persona?&quot;
* In un esempio di social media, la fonte di traffico è la piattaforma social media in uso.
   * In questo esempio, [!DNL Facebook] è il valore di origine. Altri esempi sono Twitter e Instagram. Se il supporto UTM è [!DNL Paid Search]D&#39;altra parte, l&#39;origine UTM potrebbe essere AdWords o BingAds.

* Questo parametro viene mappato su [!DNL Marketo Measure] Campo &quot;Origine punto di contatto&quot; in SFDC.
* _[!DNL Marketo Measure]Best practice:_ Questo parametro traccia la fonte del traffico, quindi non è adatto per indicare il tipo di annuncio, ad esempio retargeting, sponsorizzato, ecc. Viene utilizzato al meglio per monitorare il canale secondario di livello superiore. Ricordate, state rispondendo alla domanda &quot;Da dove viene il mio traffico?&quot; Stai cercando il referrer. In questo esempio, UTM Source è il luogo in cui si trova l’annuncio (non la pagina web effettiva, in quanto viene tracciato automaticamente al di fuori dei tag). Se tieni traccia di una campagna e-mail con calo, l’e-mail con calo è l’origine.

**utm_campaign**

* La campagna viene utilizzata per identificare una campagna di marketing specifica.
* Risponde alla domanda: &quot;Perché vengono da te?&quot;
* Utilizza questo tag per indicare il nome della campagna pubblicitaria così come esiste in [!DNL Google AdWords] o [!DNL BingAds]oppure per indicare il nome con cui identificare internamente la campagna. Puoi anche utilizzare questo tag per specificare altre informazioni come la geolocalizzazione o il tipo di rete di annunci.
* Questo parametro viene mappato su [!DNL Marketo Measure] &quot;Campo Nome campagna pubblicitaria&quot; in SFDC.
* _[!DNL Marketo Measure]Best practice_: Durante la determinazione dei nomi delle campagne, evita di utilizzare punti o spazi vuoti tra le parole, in quanto il loro utilizzo può causare errori di codifica del browser. Per ottenere risultati ottimali, utilizza invece i caratteri di sottolineatura.

**utm_content**

* Utilizza il parametro di contenuto UTM quando desideri tenere traccia di più di un elemento di marketing esistente in una singola pagina web. Ad esempio, se hai un pulsante &quot;Richiedi una demo&quot; e un pulsante &quot;Iscriviti alla nostra newsletter settimanale&quot; e vuoi sapere quale genera più traffico, assegna un nome a ciascuno di essi e utilizza un tag di contenuto UTM per tracciarli. Il nome di ogni elemento di &quot;contenuto&quot; è il valore del tag.
* Questo parametro viene mappato su [!DNL Marketo Measure] Campo &quot;Ad Content&quot; in SFDC.
* _[!DNL Marketo Measure]Best practice_: Questo è un valore facoltativo ma [!DNL Marketo Measure] consiglia di utilizzarlo. Questo tag è associato al titolo dell’annuncio o del pezzo di marketing che desideri monitorare. Se utilizzi un annuncio di immagine, accertati di scrivere le dimensioni dell’immagine nel relativo titolo.

**utm_term**

* Term è simile al parametro UTM Content . Il termine è ottimo per identificare le parole chiave negli annunci per le campagne a pagamento. Se utilizzi la funzione di assegnazione tag automatica , questa operazione viene eseguita automaticamente. Se non utilizzi la funzione di assegnazione tag automatica della piattaforma di annunci, assicurati di aggiungere con attenzione tutte le parole chiave che desideri monitorare.
* Questo parametro viene mappato su [!DNL Marketo Measure] Campo &quot;Testo con parole chiave&quot; in SFDC.
* _[!DNL Marketo Measure]Best practice_: Il tag di termine UTM è facoltativo ma ottimo per il tracciamento delle parole chiave. Controllare l&#39;ortografia e evitare di utilizzare caratteri speciali. Se è necessaria più di una parola, prova a utilizzare caratteri di sottolineatura o senza spazi.

Ogni parametro raccoglie informazioni rilevanti per il valore assegnato. Il valore di ciascun tag consente di monitorare e ordinare tutte le campagne digitali e rispondere alle domande seguenti: dove, come e perché?

Questo è un grafico dei parametri UTM [!DNL Marketo Measure] analisi e il corrispondente campo punto di contatto a cui sono associati:

| **Parametro UTM** | **Corrispondente [!DNL Marketo Measure] Campo** |
|---|---|
| utm_medium | Medium |
| utm_source | Origine punto di contatto |
| utm_campaign | Nome della campagna pubblicitaria |
| utm_content | Contenuto annuncio |
| utm_term | Testo della parola chiave |
