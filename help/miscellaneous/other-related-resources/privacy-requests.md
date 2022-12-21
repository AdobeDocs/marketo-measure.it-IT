---
description: Richieste sulla privacy - [!DNL Marketo Measure] - Documentazione del prodotto
title: Richieste sulla privacy
exl-id: 883e475f-9868-412a-b505-230556f38484
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Richieste sulla privacy {#privacy-requests}

Questo documento fornisce una panoramica sulla gestione delle singole richieste di privacy dei dati che puoi inviare a [!DNL Marketo Measure] attraverso [!DNL Privacy Service] Interfaccia utente e **[!DNL Privacy Service]API**.

Puoi inviare singole richieste per accedere e cancellare i dati dei consumatori da [!DNL Marketo Measure] in due modi:

* Attraverso il [[!DNL Privacy Service] Interfaccia](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/overview.html){target=&quot;_blank&quot;}.
* Attraverso il **[!DNL Privacy Service]API**. Consulta la documentazione [qui](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/overview.html){target=&quot;_blank&quot;} e riferimento API [qui](https://developer.adobe.com/experience-platform-apis/references/privacy-service/){target=&quot;_blank&quot;}.

La [Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html){target=&quot;_blank&quot;} supporta due tipi di richieste: accesso ai dati ed eliminazione dei dati.

Vediamo come creare le richieste di accesso ed eliminazione.

## Configurazione necessaria per inviare richieste per Marketo Measure {#required-setup-to-send-requests-for-marketo-measure}

Per effettuare richieste di accesso ed eliminazione di dati per [!DNL Marketo Measure], devi:

1. Identifica quanto segue:

   a) ID organizzazione IMS

   b) Indirizzo e-mail della persona su cui desideri agire

   Un ID organizzazione IMS è una stringa alfanumerica composta da 24 caratteri, con l&#39;aggiunta di @AdobeOrg. Se il team marketing o l’amministratore di sistema di Adobe interno non conosce l’ID organizzazione IMS della tua organizzazione, contatta l’Assistenza clienti Adobe all’indirizzo gdprsupport@adobe.com. Per inviare richieste all’API Privacy è necessario l’ID organizzazione IMS.

1. In [!DNL Privacy Service], puoi inviare le richieste di accesso ed eliminazione a [!DNL Marketo Measure]e controlla lo stato delle richieste esistenti.

## Valori campo obbligatori in [!DNL Marketo Measure] Richieste JSON {#required-field-values-in-marketo-measure-json-requests}

&quot;companyContexts&quot;:

* &quot;namespace&quot;: **imsOrgID**
* &quot;value&quot;: `<Your IMS Org ID Value>`

&quot;utenti&quot;:

* &quot;action&quot;: o [!UICONTROL access] o eliminare
* &quot;userIDs&quot;:
   * &quot;namespace&quot;: email
   * &quot;type&quot;: standard
   * &quot;value&quot;: `<Data Subject's Email Address>`

&quot;include&quot;:

* **marketoMeasure** (che è il prodotto Adobe che si applica alla richiesta)

&quot;regolamento&quot;:

* **rgpd**, **ccpa**, **pdpa**, **lgpd_bra** oppure **nzpa_nzl** (regolamento sulla privacy applicabile alla richiesta)

## Esempio 1: Richiesta di cancellazione RGPD {#gdpr-delete-request}

Richiesta JSON

```text
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "delete"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "gdpr",
}
```

Risposta JSON

```text
{
  "requestId": "16331241037112570RX-245",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "997b01e3-9568-402c-904b-b4e60a437875",
      "customer": {
        "user": {
          "action": [
            "delete"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```

## Esempio 2: Richiesta di accesso CCPA {#ccpa-access-request}

Richiesta JSON

```text
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "access"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "ccpa",
}
```

Risposta JSON

```text
{
  "requestId": "16329573462631890RX-207",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "3115e42d-011b-47ab-a2b0-ed4356af4d3e",
      "customer": {
        "user": {
          "action": [
            "access"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```
