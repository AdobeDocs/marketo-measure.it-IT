---
description: Dati raccolti da JavaScript - [!DNL Marketo Measure] - Documentazione del prodotto
title: Dati raccolti da JavaScript
feature: Tracking
source-git-commit: 2be08b96fb9f6d027e80751db64f16a7f2893764
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 6%

---

# Dati raccolti da JavaScript {#data-collected-by-javascript}

Scopri i dati raccolti da JavaScript di Marketo Measure durante la distribuzione.

**Richiesta di esempio:**

```
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure raccoglie i seguenti dati comuni per tutti i tipi di richieste:

<table>
<thead>
  <tr>
    <th>Origine</th>
    <th>Nome</th>
    <th>Tipo di dati</th>
    <th>Finalità</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Intestazione richiesta</td>
    <td>Indirizzo IP</td>
    <td>stringa</td>
    <td>La posizione dell’utente viene dedotta tramite la ricerca GeoIP. Questi dati sono temporanei e non vengono memorizzati in modo permanente.</td>
  </tr>
  <tr>
    <td>Intestazione richiesta</td>
    <td>Stringa dell’agente utente</td>
    <td>stringa</td>
    <td>Determina il dispositivo utilizzato dall'utente.</td>
  </tr>
  <tr>
    <td>Parametro query</td>
    <td>_biz_u</td>
    <td>stringa</td>
    <td>ID cookie Bizible</td>
  </tr>
  <tr>
    <td>Parametro query</td>
    <td>_biz_l</td>
    <td>stringa</td>
    <td>URL della pagina corrente</td>
  </tr>
  <tr>
    <td>Parametro query</td>
    <td>_biz_t</td>
    <td>long</td>
    <td>Timestamp attività</td>
  </tr>
  <tr>
    <td>Parametro query</td>
    <td>_biz_i</td>
    <td>stringa</td>
    <td>Titolo pagina corrente</td>
  </tr>
</tbody>
</table>

Oltre ai dati comuni di cui sopra, bizible.js aggiunge anche dati aggiuntivi a seconda dei tipi di richiesta specificati di seguito:

<table>
<thead>
  <tr>
    <th>Tipo di richiesta</th>
    <th>Percorso richiesta</th>
    <th>Parametro di query aggiuntivo</th>
    <th>Tipo di dati</th>
    <th>Finalità</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Pageview</td>
    <td>/ipv</td>
    <td>_biz_r</td>
    <td>stringa</td>
    <td>URL della pagina di provenienza.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_h</td>
    <td>stringa</td>
    <td>Risoluzione dello schermo del client con hash.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_c</td>
    <td>stringa</td>
    <td>Parametro facoltativo. Se questo parametro è presente, indica che il tenant configura bizible.js per attendere il consenso degli utenti prima del tracciamento e che bizible.js ha ricevuto il consenso degli utenti per essere tracciato.</td>
  </tr>
  <tr>
    <td>Invii modulo</td>
    <td>/frm</td>
    <td>e-mail</td>
    <td>stringa</td>
    <td>Indirizzo e-mail in testo normale.</td>
  </tr>
  <tr>
    <td>Mappatura ID utente</td>
    <td>/u</td>
    <td>mapType</td>
    <td>enum</td>
    <td>Che tipo di mappatura ID utente è stato rilevato bizible.js (ID Marketo munchkin e ECID Adobe)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>mapValue</td>
    <td>stringa</td>
    <td>Il valore ID effettivo del cookie di terze parti dell’integrazione di cui sopra.</td>
  </tr>
</tbody>
</table>

>[!NOTE]
>
>Bizible è il nome precedente di Marketo Measure.
