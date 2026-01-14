---
description: Dati raccolti dalle linee guida di JavaScript per gli utenti di Marketo Measure
title: Dati raccolti da JavaScript
feature: Tracking
exl-id: 83814168-9d3e-45ac-b514-df58f0b2e90b
hidefromtoc: true
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 12%

---

# Dati raccolti da JavaScript {#data-collected-by-javascript}

Scopri i dati raccolti da Marketo Measure JavaScript durante la distribuzione.

**Richiesta di esempio:**

```text
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure raccoglie i seguenti dati comuni per tutti i tipi di richieste:

| Origine | Nome | Tipo di dati | Finalità |
| --- | --- | --- | --- |
| Intestazione richiesta | Indirizzo IP | stringa | La posizione dell’utente viene dedotta tramite la ricerca GeoIP. Questi dati sono temporanei e non vengono memorizzati in modo permanente. |
| Intestazione richiesta | Stringa dell’agente utente | stringa | Determina il dispositivo utilizzato dall&#39;utente. |
| Parametri query | `_biz_u` | stringa | ID cookie Bizible. |
| Parametri query | `_biz_l` | stringa | URL della pagina corrente. |
| Parametri query | `_biz_t` | long | Timestamp dell’attività. |
| Parametri query | `_biz_i` | stringa | Titolo della pagina corrente. |

Oltre ai dati comuni di cui sopra, bizible.js aggiunge anche dati aggiuntivi a seconda dei tipi di richiesta specificati di seguito:

| Tipo di richiesta | Percorso richiesta | Parametro di query aggiuntivo | Tipo di dati | Finalità |
| --- | --- | --- | --- | --- |
| Pageview | `/ipv` | `_biz_r` | stringa | URL della pagina di provenienza. |
|  |  | `_biz_h` | stringa | Risoluzione dello schermo del client con hash. |
|  |  | `_biz_c` | stringa | Parametro facoltativo. Se questo parametro è presente, indica che il tenant configura `bizible.js` per attendere il consenso dell&#39;utente prima del tracciamento e che `bizible.js` ha ricevuto il consenso dell&#39;utente per essere tracciato. |
| Invii modulo | `/frm` | `eMail` | stringa | Indirizzo e-mail in testo normale. |
| Mappatura ID utente | `/u` | `mapType` | enum | Che tipo di mappatura ID utente `bizible.js` ha rilevato (Marketo Munchkin ID e Adobe ECID) |
|  |  | `mapValue` | stringa | Il valore ID effettivo del cookie di terze parti dell’integrazione di cui sopra. |

>[!NOTE]
>
>Bizible è il nome precedente di Marketo Measure.
