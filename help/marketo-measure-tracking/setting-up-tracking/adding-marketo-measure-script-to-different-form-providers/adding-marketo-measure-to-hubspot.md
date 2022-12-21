---
unique-page-id: 18874759
description: Aggiunta [!DNL Marketo Measure] a [!DNL Hubspot] - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] a [!DNL Hubspot]
exl-id: 633e7ef7-7959-461e-881f-dcc543595b66
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] a [!DNL Hubspot] {#adding-marketo-measure-to-hubspot}

Scopri come aggiungere il [!DNL Marketo Measure] JavaScript per tenere traccia del [!DNL Hubspot] pagine di destinazione e invii di moduli.

Hubspot è un po&#39; diverso da altri sistemi di automazione marketing in quanto può ospitare le tue pagine di destinazione / moduli E il tuo sito web. È importante notare che le seguenti istruzioni sono per avere [!DNL Marketo Measure] tracciare l’attività su [!DNL Hubspot]Pagine ospitate. Se si alimenta il sito web con un CMS diverso da [!DNL Hubspot] (ad esempio Wordpress), è necessario aggiungere il [!DNL Marketo Measure] JavaScript anche per quel CMS.

>[!NOTE]
>
>Se distribuisci JavaScript tramite un provider di gestione dei tag come [!DNL Google Tag Manager], non è necessario codificare manualmente il [!DNL Marketo Measure] JavaScript nel tuo sito web.

## Introduzione {#getting-started}

Una volta effettuato l’accesso al [!DNL Hubspot] , segui questi passaggi.

1. Passa a Contenuto .

1. Clic **[!UICONTROL Content Settings]**.

1. Within [!UICONTROL Content Settings], fai clic su Site Header HTML (vedi immagine qui sotto).

1. Aggiungi il seguente script all’interno del `<header>`:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

   Dovrebbe essere così:

```text
<!-- Marketo Measure Javascript -->
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="">
```

>[!TIP]
>
>In quest’area potrebbero essere già presenti altri frammenti di codice di tracciamento, ad esempio un codice Google Analytics. Assicurati di separarli con un punto e virgola `;` e un singolo spazio, come questo:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`
