---
title: Proprietà delle forme di raggruppamento
description: Si apprenderà che le forme raggruppamento sono una delle forme che è possibile usare per visualizzare una classe di dominio in un linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 745101605ac4136cbb9823262367bb5bc2e2baf3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637595"
---
# <a name="properties-of-compartment-shapes"></a>Proprietà delle forme di raggruppamento
Le forme raggruppamento sono una delle forme che è possibile usare per visualizzare una classe di dominio in un linguaggio specifico di dominio. È possibile espandere e comprimere i raggruppamenti.

 Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [Personalizzazione](../modeling/customizing-and-extending-a-domain-specific-language.md)ed estensione di un Domain-Specific language .

 Le forme raggruppamento hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Stato di compressione espansione predefinito|Se `Expanded` , i raggruppamenti vengono visualizzati al momento della creazione. Se `Collapsed` , non lo sono.|Esteso|
|Colore riempimento|Colore di riempimento della forma.|White|
|Modalità sfumatura di riempimento|Modalità sfumatura di riempimento di questa forma.|Ridimensionamento orizzontale|
|Geometria|Geometria di questa forma (rettangolo o rettangolo arrotondato).|Rettangolo|
|Dispone di punti di connessione predefiniti|Se , la forma userà i punti di connessione `True` superiore, inferiore, sinistro e destro nella finestra di progettazione generata.|Falso|
|È visibile l'intestazione a raggruppamento singolo|Se `False` e la forma ha un singolo raggruppamento, l'intestazione del raggruppamento non è visibile.|Vero|
|Colore contorno|Colore del contorno di questa forma.|Nero|
|Stile tratteggio contorno|Stile del trattino del contorno di questa forma (Tinta unita, Tratteggio, Punto, DashDot, DashDotDot, Personalizzato).|Tinta unita|
|Spessore del contorno|Spessore del contorno di questa forma.|0.03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Livello di accesso della forma raggruppamento ( `public` o `internal` ).|Pubblico|
|Attributi personalizzati|Usato per aggiungere attributi alla classe del codice sorgente generata da questa forma raggruppamento|\<none>|
|Genera una derivazione doppia|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dalla forma raggruppamento ( `none` o `abstract` `sealed` ).|Nessuno|
|Forma raggruppamento di base|Classe di base di questa forma.|(nessuna)|
|Nome|Nome della forma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa forma.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (fissa, variabile o nessuna). Se fixed, il valore della proprietà viene usato come descrizione comando; se variabile, la descrizione comando `Fixed Tooltip Text` viene definita nel codice personalizzato.|Nessuno|
|Note|Note informali associate a questa forma.|\<none>|
|Altezza iniziale|Altezza iniziale della forma, in pollici. Per le forme raggruppamento, questa è solo l'altezza della sezione dell'intestazione e non può essere ridimensionata.|1|
|Larghezza iniziale|Larghezza iniziale della forma, espressa in pollici.|1.5|
|Proprietà Exposed Fill Color As<br /><br /> Modalità sfumatura di riempimento esposta<br /><br /> Proprietà Exposed Outline Color As<br /><br /> Proprietà Exposed Outline Dash Style As<br /><br /> Proprietà Exposed Outline Thickness As<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà specificata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposto**.|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<none>|
|Correzione del testo della descrizione comando|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave usata per indicizzare la Guida di F1 per questa forma.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))