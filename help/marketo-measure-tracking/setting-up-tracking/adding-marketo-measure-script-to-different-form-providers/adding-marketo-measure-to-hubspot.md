---
unique-page-id: 18874759
description: Aggiunta di  [!DNL Marketo Measure] a [!DNL Hubspot] - [!DNL Marketo Measure] in corso
title: Aggiunta di  [!DNL Marketo Measure]  a  [!DNL Hubspot]
exl-id: 633e7ef7-7959-461e-881f-dcc543595b66
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 1%

---

# Aggiunta di [!DNL Marketo Measure] a [!DNL Hubspot] {#adding-marketo-measure-to-hubspot}

Scopri come aggiungere il JavaScript [!DNL Marketo Measure] per tenere traccia delle pagine di destinazione di [!DNL Hubspot] e inviare moduli.

Hubspot è un po’ diverso da altri sistemi di automazione marketing in quanto può ospitare le pagine di destinazione / moduli E il tuo sito web. È importante notare che le seguenti istruzioni sono per avere [!DNL Marketo Measure] attività di tracciamento sulle pagine ospitate da [!DNL Hubspot]. Se si alimenta il sito Web con un CMS diverso da [!DNL Hubspot] (ad esempio, Wordpress), è necessario aggiungere anche il JavaScript [!DNL Marketo Measure] a tale CMS.

>[!NOTE]
>
>Se si distribuisce JavaScript tramite un provider di gestione tag come [!DNL Google Tag Manager], non è necessario codificare manualmente il JavaScript [!DNL Marketo Measure] nel sito Web.

## Guida introduttiva {#getting-started}

Dopo aver effettuato l&#39;accesso all&#39;account [!DNL Hubspot], eseguire la procedura seguente.

1. Passa a Contenuto.

1. Fare clic su **[!UICONTROL Content Settings]**.

1. In [!UICONTROL Content Settings], fare clic su HTML intestazione sito (vedere l&#39;immagine seguente).

1. Aggiungi il seguente script in `<header>`:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

   Dovrebbe essere simile al seguente:

```text
<!-- Marketo Measure Javascript -->
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="">
```

>[!TIP]
>
>In quest’area potrebbero già essere presenti altri snippet di codice di tracciamento, ad esempio un codice Google Analytics. Assicurarsi di separarli con un punto e virgola `;` e un singolo spazio, come segue:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`
