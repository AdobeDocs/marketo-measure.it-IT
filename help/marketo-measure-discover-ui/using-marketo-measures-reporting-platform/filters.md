---
unique-page-id: 18874656
description: Filtri - [!DNL Marketo Measure] - Documentazione del prodotto
title: Filtri
exl-id: 249266c8-9ff5-4895-979c-4f377423d031
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Filtri {#filters}

Scopri di più sui diversi filtri disponibili in Scopri e come utilizzarli.

>[!NOTE]
>
>Gli operatori &quot;corrisponde a un attributo utente&quot; e &quot;corrisponde a (avanzato)&quot; all’interno dei filtri Discover sono puramente amministrativi e possono essere ignorati in modo sicuro.

**ID account**

_Utilizzato in: Marketing basato su account_

Seleziona o incolla una serie di ID account dal CRM per filtrare i risultati. Gli ID account forniscono una maggiore univocità rispetto a Nome account, poiché i nomi possono essere gli stessi.

**Nome account**

_Utilizzato in: Marketing basato su account_

Seleziona o incolla una serie di nomi di account dal CRM per filtrare i risultati. Le stringhe possono avere duplicati, quindi è possibile avere più &quot;[!DNL Marketo Measure]&quot;, ad esempio. Se in questo caso è necessario un singolo account, utilizza invece il filtro ID account .

**Modello di attribuzione**

_Utilizzato in: Panoramica, spese di marketing, ROI degli annunci, marketing basato su account, traffico web, CMO, media a pagamento, marketing dei contenuti, passaporto_

Scegliete un singolo modello di attribuzione da applicare alla bacheca: Primo contatto, contatto per la creazione di lead, a forma di U, a forma di W, a percorso completo o a modello personalizzato. Percorso completo e modello personalizzato non sono disponibili su tutti i livelli.

**Campaign**

_Utilizzato in: Panoramica, crescita, ROI annunci, traffico web, CMO, media a pagamento, marketing contenuti, Passport_

Filtrate la bacheca per uno o più nomi di campagne. Gli operatori offrono al filtro una flessibilità aggiuntiva, ad esempio utilizzando gli operatori &quot;contiene&quot; o &quot;inizia con&quot;. Se è stato applicato un filtro Canale o Sottocanale, l’elenco delle campagne visualizzate sarà un sottoinsieme dei filtri applicati.

**Categoria 1-10**

_Utilizzato in: Panoramica, crescita, ROI annunci, CMO, media a pagamento, marketing dei contenuti, Velocity, snapshot, funnel coorte, Passport_

Applicate filtri di segmento alla bacheca, utilizzando le categorie e i segmenti creati nella [!DNL Marketo Measure] Impostazioni. L’elenco delle categorie create verrà visualizzato nel menu dei filtri, pertanto se non è stata impostata alcuna categoria, nel menu non saranno presenti filtri di categoria. Le categorie di segmenti non sono disponibili in tutti i livelli e il numero di categorie disponibili varia anche in base al livello.

**Canale**

_Utilizzato in: Panoramica, crescita, spesa marketing, ROI degli annunci, traffico web, CMO, media a pagamento, marketing dei contenuti, Velocity, Passport_

Filtrate la bacheca per uno o più canali. Gli operatori offrono al filtro una flessibilità aggiuntiva, ad esempio utilizzando gli operatori &quot;contiene&quot; o &quot;inizia con&quot;. Una volta inserito un canale, i valori mostrati nei filtri Subchannel e Campaign verranno ricavati dal filtro del canale secondario applicato.

**Fase coorte**

_Utilizzato in: Funnel coorte_

Seleziona l’area di visualizzazione di cui desideri visualizzare una coorte. L’area di visualizzazione selezionata verrà visualizzata nella parte superiore dell’imbuto, con tutte le conversioni che scorrono dall’alto verso il basso.

**Data**

_Utilizzato in: Panoramica, crescita, spesa marketing, ROI degli annunci, marketing basato su account, traffico web, CMO, media a pagamento, marketing dei contenuti, Velocity, snapshot, funnel coorte, Passport_

Seleziona un intervallo di date per filtrare i dati nelle bacheche, utilizzando operatori di date flessibili come ad esempio &quot;è nell’intervallo&quot; &quot;è nell’anno&quot;, &quot;è nell’anno&quot; o &quot;è prima&quot;. L’eccezione è Istantanea, in cui verrà selezionata una singola data per visualizzare un’istantanea dei dati.

**Tipo di data**

_Utilizzato in: Panoramica, crescita, spesa marketing, ROI degli annunci, marketing basato su account, traffico web, CMO, media a pagamento, marketing dei contenuti, Passport_

Scegliere il tipo di data da utilizzare, associato al filtro Data. Il tipo di data predefinito varia a seconda della bacheca. Per data punto di contatto si intende la data in cui è avvenuta l’attività di marketing, Data creazione è la data in cui è stato creato il lead o il contatto o l’opportunità nel CRM e Data chiusura è la data in cui l’opportunità è stata chiusa.

**Dimensione**

_Utilizzato in: Supporti a pagamento_

Il Dimension è simile alla funzione Raggruppa per, con la differenza che viene utilizzato sulla scheda Media a pagamento in modo leggermente diverso. Anziché sovrapporre un grafico, il Dimension modifica le linee del grafico Panoramica e l’oggetto iniziale delle tabelle.

![](assets/1.png)

Per impostazione predefinita, il Dimension è impostato su Subchannel e può essere modificato in:

* Nessuno: Visualizza tutti gli elementi aggregati senza interruzioni
* Canale: Elenca i dati per canale di marketing
* Canale secondario: Elenca i dati per canale secondario di marketing
* Campagna: Elenca i dati per campagna
* Account: Elenca i dati per account. Si applica a [!DNL AdWords], [!DNL Bing]e [!DNL Facebook].
* Gruppo di annunci: Elenca i dati per gruppo di annunci. Si applica a [!DNL AdWords], [!DNL Bing]e [!DNL Facebook].
* Annuncio: Elenca i dati per annuncio. Si applica agli annunci Doubleclick, quindi se Doubleclick non è utilizzato, non verrà visualizzato alcun risultato
* Inserzionista: Elenca i dati per inserzionista. Si applica all&#39;inserzionista Doubleclick, quindi se Doubleclick non è utilizzato, non verrà visualizzato alcun risultato
* Creativo: Elenca i dati per creativo. Si applica a [!DNL AdWords], [!DNL Bing]e [!DNL Facebook].
* Parola chiave: Elenca i dati per parola chiave. Si applica a [!DNL AdWords], [!DNL Bing]e [!DNL Facebook].
* Posizionamento: Elenca i dati in base al posizionamento. Si applica ai posizionamenti Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato
* Sito: Elenca i dati per sito. Si applica ai siti Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato

**Raggruppa per**

_Utilizzato in: Panoramica, crescita, spesa marketing, marketing basato su account, traffico web, CMO_

Consente di regolare i grafici per modificare la dimensione sovrapposta e raggruppata. Per impostazione predefinita, Raggruppa per è impostato su Canale e può essere modificato in:

* Nessuno: Visualizza tutti gli elementi aggregati senza interruzioni
* Canale: Raggruppa i dati per canale di marketing
* Canale secondario: Raggruppa i dati per canale secondario marketing
* Campagna: Raggruppa i dati per campagna
* Account: Raggruppa i dati per account. Si applica a [!DNL AdWords], [!DNL Bing]e [!DNL Facebook].
* Gruppo di annunci: Raggruppa i dati per gruppo di annunci. Si applica a [!DNL AdWords], [!DNL Bing]e [!DNL Facebook].
* Annuncio: Raggruppa i dati per annuncio. Si applica agli annunci Doubleclick, quindi se Doubleclick non è utilizzato, non verrà visualizzato alcun risultato
* Inserzionista: Raggruppa i dati per inserzionista. Si applica all&#39;inserzionista Doubleclick, quindi se Doubleclick non è utilizzato, non verrà visualizzato alcun risultato
* Creativo: Raggruppa i dati per creativo. Si applica a [!DNL AdWords], [!DNL Bing]e [!DNL Facebook].
* Parola chiave: Raggruppa i dati per parola chiave. Si applica a [!DNL AdWords], [!DNL Bing]e [!DNL Facebook].
* Posizionamento: Raggruppa i dati per posizione. Si applica ai posizionamenti Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato
* Sito: Raggruppa i dati per sito. Si applica ai siti Doubleclick, quindi se Doubleclick non viene utilizzato, non verrà visualizzato alcun risultato

![](assets/2.png)

**Pagina di destinazione**

_Utilizzato in: Marketing dei contenuti_

Approfondisci le prestazioni di una singola pagina di destinazione o, forse, delle pagine di destinazione che contengono una determinata parola, ad esempio &quot;blog&quot;.

**Metrica**

_Utilizzato in: Panoramica, Traffico web, CMO, Media a pagamento, Marketing dei contenuti_

Esistono due selettori di metriche diverse che vengono utilizzati su diverse bacheche. Il selettore delle metriche modifica la misura in un grafico, in modo da poter passare, ad esempio, dalla visualizzazione di entrate, spese o impression.

Nelle bacheche Panoramica e CMO è disponibile un elenco abbreviato di valori relativi alle metriche ROI:

* Entrate
* Spesa
* Offerte
* Ricavi dalla pipeline
* Opportunità
* Contatti
* Lead

Nelle bacheche Traffico web, File multimediali a pagamento e Content Marketing è disponibile un elenco più lungo di valori relativi alle metriche ROI e funnel:

* Entrate
* Spesa
* Offerte
* Ricavi dalla pipeline
* Opportunità
* Contatti
* Lead
* Clic
* impression
* Visite
* Visite univoche
* Visualizzazioni pagina
* Forms

**Fase**

_Utilizzato in: Velocity_

Per impostazione predefinita, la bacheca di Velocity visualizza i tempi di tutte le fasi, ma per eseguire il drill-in a uno specifico stadio, utilizzate il filtro Stage per selezionare l&#39;area di visualizzazione.

**Canale secondario**

_Utilizzato in: Panoramica, crescita, spesa marketing, ROI degli annunci, traffico web, CMO, media a pagamento, marketing dei contenuti, Passport_

Filtrate la bacheca per uno o più sottocanali. Gli operatori offrono al filtro una flessibilità aggiuntiva, ad esempio utilizzando gli operatori &quot;contiene&quot; o &quot;inizia con&quot;. Se è stato applicato un filtro Canale, l’elenco dei sottocanali visualizzati sarà un sottoinsieme dei filtri applicati. Una volta inserito un canale secondario, i valori mostrati nei filtri Campagna saranno ricavati dal filtro del canale secondario applicato.

**URL**

_Utilizzato in: Traffico web_

Approfondisci il traffico di un singolo URL o forse degli URL che contengono una determinata parola, ad esempio &quot;product&quot;.

**Vinto**

_Utilizzato in: Velocity_

Per impostazione predefinita, la scheda Velocity riporta solo le opportunità di vincita chiuse, ma regola questo filtro per vedere la velocità delle opportunità di vincita o di perdita chiuse chiuse.
