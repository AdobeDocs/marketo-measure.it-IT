---
unique-page-id: 18874656
description: Filtri - [!DNL Marketo Measure] - Documentazione del prodotto
title: Filtri
exl-id: 249266c8-9ff5-4895-979c-4f377423d031
feature: Reporting
source-git-commit: e24e01a03218252c06c9a776e0519afbddbe2b8c
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 1%

---

# Filtri {#filters}

Scopri di più sui diversi filtri disponibili in Scopri e come utilizzarli.

>[!NOTE]
>
>Gli operatori &quot;corrisponde a un attributo utente&quot; e &quot;corrisponde a (avanzato)&quot; all’interno dei filtri di individuazione sono puramente amministrativi e possono essere tranquillamente ignorati.

**ID account**

_Utilizzato in: marketing basato sull’account_

Seleziona o incolla una serie di ID account dal CRM per filtrare i risultati. Gli ID account forniscono maggiore univocità rispetto al nome account, in quanto i nomi possono essere uguali.

**Nome account**

_Utilizzato in: marketing basato sull’account_

Seleziona o incolla una serie di nomi account dal CRM per filtrare i risultati. Le stringhe possono avere duplicati, quindi è possibile avere più elementi &quot;[!DNL Marketo Measure]&quot; ad esempio. Se in questo caso è necessario un singolo account, utilizza invece il filtro ID account.

**Modello di attribuzione**

_Utilizzato in: Panoramica, Spese di marketing, ROI annunci, Marketing basato su account, Traffico web, CMO, Supporti a pagamento, Marketing dei contenuti, Passport_

Scegli un singolo modello di attribuzione da applicare alla bacheca: Primo contatto, Tocco creazione lead, A forma di U, A forma di W, Percorso completo o Modello personalizzato. Il percorso completo e il modello personalizzato non sono disponibili su tutti i livelli.

**Campaign**

_Utilizzato in: Panoramica, Crescita, ROI annunci, Traffico web, CMO, Supporti a pagamento, Marketing dei contenuti, Passport_

Filtra la bacheca in base a uno o più nomi di campagna. Gli operatori offrono al filtro ulteriore flessibilità, ad esempio utilizzando gli operatori &quot;contiene&quot; o &quot;inizia con&quot;. Se è stato applicato un filtro Canale o Sottocanale, l’elenco delle campagne visualizzate sarà un sottoinsieme dei filtri applicati.

**Categoria 1-10**

_Utilizzato in: Panoramica, Crescita, ROI annunci, CMO, Paid Media, Content Marketing, Velocity, Snapshot, Cohort Funnel, Passport_

Applica i filtri segmento alla bacheca, utilizzando le Categorie e i Segmenti creati in [!DNL Marketo Measure] Impostazioni. L&#39;elenco delle Categorie create verrà visualizzato nel menu dei filtri, quindi se non è stata impostata alcuna Categoria, nel menu non sarà presente alcun filtro Categoria. Le categorie di segmenti non sono disponibili in tutti i livelli e anche il numero di categorie disponibili varia in base al livello.

**Canale**

_Utilizzato in: Panoramica, Crescita, Spesa marketing, ROI annunci, Traffico web, CMO, Supporti a pagamento, Marketing dei contenuti, Velocity, Passport_

Filtra la scheda per uno o più canali. Gli operatori offrono al filtro ulteriore flessibilità, ad esempio utilizzando gli operatori &quot;contiene&quot; o &quot;inizia con&quot;. Una volta inserito un canale, i valori mostrati nei filtri Subchannel e Campaign provengono dal filtro subchannel applicato.

**Fase coorte**

_Utilizzato in: Funnel coorte_

Selezionare l&#39;area di visualizzazione di cui si desidera visualizzare una coorte. L’area di visualizzazione selezionata apparirà nella parte superiore dell’imbuto, con tutte le conversioni che scorrono dalla parte superiore.

**Data**

_Utilizzato in: Panoramica, Crescita, Spese di marketing, ROI annunci, Marketing basato su account, Traffico web, CMO, Paid Media, Marketing dei contenuti, Velocity, Snapshot, Funnel coorte, Passport_

Seleziona un intervallo di date per filtrare i dati nelle bacheche, utilizzando operatori di date flessibili come, ad esempio, &quot;è nell’intervallo&quot;, &quot;è nell’anno&quot; o &quot;è prima&quot;. L&#39;eccezione è Snapshot, in cui è possibile selezionare una singola data per visualizzare un&#39;istantanea dei dati.

**Tipo di data**

_Utilizzato in: Panoramica, Crescita, Spese di marketing, ROI annunci, Marketing basato su account, Traffico web, CMO, Supporti a pagamento, Marketing dei contenuti, Passport_

Scegliere il tipo di data da utilizzare, associato al filtro Data. Il tipo di data predefinito varia in base alla bacheca. Data punto di contatto si riferisce alla data in cui è avvenuta l’attività di marketing, Data di creazione è la data in cui il lead, il contatto o l’opportunità è stato creato nel CRM e Data di chiusura è la data in cui l’opportunità è stata chiusa.

**Dimensione**

_Utilizzato in: File multimediali a pagamento_

La funzione Dimension è simile alla funzione Raggruppa per, con la differenza che viene utilizzata nella scheda File multimediali pagati in modo leggermente diverso. Anziché impilare un grafico, Dimension modifica le linee del grafico Panoramica e l&#39;oggetto iniziale delle tabelle.

![](assets/1.png)

Per impostazione predefinita, Dimension è impostato su Sottocanale e può essere modificato in:

* Nessuno: visualizza tutto in forma aggregata senza suddivisioni
* Canale: elenca i dati per canale di marketing
* Sottocanale: elenca i dati per sottocanale di marketing
* Campagna: elenca i dati per campagna
* Account: elenca i dati per account. Applicabile a [!DNL AdWords], [!DNL Bing], e [!DNL Facebook].
* Gruppo di annunci: elenca i dati per gruppo di annunci. Applicabile a [!DNL AdWords], [!DNL Bing], e [!DNL Facebook].
* Ad: elenca i dati per annuncio. Si applica agli annunci Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato
* Inserzionista: elenca i dati per inserzionista. Si applica all’inserzionista Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato
* Creativo: elenca i dati per creativo. Applicabile a [!DNL AdWords], [!DNL Bing], e [!DNL Facebook].
* Parola chiave: elenca i dati per parola chiave. Applicabile a [!DNL AdWords], [!DNL Bing], e [!DNL Facebook].
* Posizionamento: elenca i dati in base al posizionamento. Si applica ai posizionamenti Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato
* Sito: elenca i dati per sito. Si applica ai siti Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato

**Raggruppa per**

_Utilizzato in: Panoramica, Crescita, Spesa marketing, Marketing basato su account, Traffico web, CMO_

Regola i grafici per modificare le dimensioni che vengono sovrapposte e raggruppate. Per impostazione predefinita, Raggruppa per è impostato su Canale e può essere modificato in:

* Nessuno: visualizza tutto in forma aggregata senza suddivisioni
* Canale: raggruppa i dati per canale di marketing
* Sottocanale: raggruppa i dati per sottocanale di marketing
* Campagna: raggruppa i dati per campagna
* Conto: raggruppa i dati per conto. Applicabile a [!DNL AdWords], [!DNL Bing], e [!DNL Facebook].
* Gruppo di annunci: raggruppa i dati per gruppo di annunci. Applicabile a [!DNL AdWords], [!DNL Bing], e [!DNL Facebook].
* Annuncio: raggruppa i dati per annuncio. Si applica agli annunci Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato
* Inserzionista: raggruppa i dati per inserzionista. Si applica all’inserzionista Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato
* Creativo: raggruppa i dati per creativo. Applicabile a [!DNL AdWords], [!DNL Bing], e [!DNL Facebook].
* Parola chiave: raggruppa i dati per parola chiave. Applicabile a [!DNL AdWords], [!DNL Bing], e [!DNL Facebook].
* Posizionamento: raggruppa i dati in base al posizionamento. Si applica ai posizionamenti Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato
* Sito: raggruppa i dati per sito. Si applica ai siti Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato

![](assets/2.png)

**Pagina di destinazione**

_Utilizzato in: Marketing dei contenuti_

Approfondisci le prestazioni di una singola pagina di destinazione, o forse di pagine di destinazione che contengono una certa parola come &quot;blog&quot;.

**Metrica**

_Utilizzato in: Panoramica, Traffico web, CMO, Supporti a pagamento, Content Marketing_

Esistono due selettori di metriche diversi utilizzati in pannelli diversi. Il selettore delle metriche modifica la misura in un grafico, in modo da poter alternare, ad esempio, la visualizzazione delle entrate o delle spese o delle impression.

Nelle schede Panoramica e CMO, è disponibile un elenco ridotto di valori relativi alle metriche ROI:

* Ricavi
* Spesa
* Offerte
* Ricavi pipeline
* Opportunità
* Contatti
* Lead

Sulle bacheche Traffico web, Contenuti multimediali a pagamento e Marketing dei contenuti, è disponibile un elenco più lungo di valori relativi sia al ROI che alle metriche funnel:

* Ricavi
* Spesa
* Offerte
* Ricavi pipeline
* Opportunità
* Contatti
* Lead
* Clic
* impressioni
* Visite
* Visite univoche
* Visualizzazioni pagina
* Forms

**Fase**

_Utilizzato in: Velocity_

Per impostazione predefinita, la scheda Velocity visualizza i tempi per tutti gli stadi, ma per eseguire il drill-in a uno stadio specifico, utilizzate il filtro Stadio per selezionare lo stadio.

**Sottocanale**

_Utilizzato in: Panoramica, Crescita, Spesa marketing, ROI annunci, Traffico web, CMO, Supporti a pagamento, Marketing dei contenuti, Passport_

Filtra la scheda in base a uno o più sottocanali. Gli operatori offrono al filtro ulteriore flessibilità, ad esempio utilizzando gli operatori &quot;contiene&quot; o &quot;inizia con&quot;. Se è stato applicato un filtro Canale, l’elenco dei canali secondari visualizzati sarà un sottoinsieme dei filtri applicati. Una volta inserito un sottocanale, i valori mostrati nei filtri di Campaign provengono dal filtro del sottocanale applicato.

**URL**

_Utilizzato in: Traffico web_

Approfondisci il traffico di un singolo URL, o forse URL che contengono una certa parola come &quot;prodotto&quot;.

**Vincitore**

_Utilizzato in: Velocity_

Per impostazione predefinita, la bacheca Velocity riporta solo le opportunità realizzate chiuse, ma regola questo filtro per esaminare la velocità delle opportunità realizzate chiuse o perse chiuse.
