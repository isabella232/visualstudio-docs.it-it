---
title: Proprietà delle forme delle porte
description: Informazioni sulle forme porta e su come usare le forme porta per rappresentare le classi di dominio nella finestra di progettazione generata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 3aff5311231069b2fa51feebd1124f2b20e8b707
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637492"
---
# <a name="properties-of-port-shapes"></a>Proprietà delle forme delle porte
È possibile usare forme porta per rappresentare classi di dominio nella finestra di progettazione generata.

 Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione [di un Domain-Specific linguaggio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Le forme porta hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento|Colore di riempimento della forma.|White|
|Modalità sfumatura di riempimento|Modalità sfumatura di riempimento di questa forma.|Ridimensionamento orizzontale|
|Geometria|Geometria di questa forma (Rettangolo, Rettangolo arrotondato, Ellisse o Cerchio).|Rettangolo|
|Dispone di punti di connessione predefiniti|Se , la forma userà i punti di connessione `True` superiore, inferiore, sinistro e destro nella finestra di progettazione generata.|Falso|
|Colore del contorno|Colore del contorno di questa forma.|Nero|
|Stile tratteggio del contorno|Stile del tratteggio del contorno di questa forma (Tinta unita, Trattino, Punto, DashDot, DashDotDot o Personalizzato).|Tinta unita|
|Spessore del contorno|Spessore del contorno di questa forma.|0.03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Livello di accesso della classe ( `public` o `internal` ).|Pubblico|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe del codice sorgente generata da questa forma.|\<none>|
|Genera un valore derivato da Double|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dalla porta ( `none` , `abstract` o `sealed` ).|Nessuno|
|Porta di base|Classe di base di questa forma.|(nessuna)|
|Nome|Nome della forma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi associato a questa forma.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (fissa, variabile o nessuna). Se fixed, il valore della proprietà viene usato come descrizione `Fixed Tooltip Text` comando; se variabile, la descrizione comando viene definita nel codice personalizzato.|Nessuno|
|Note|Note informali associate a questa forma.|\<none>|
|Altezza iniziale|Altezza iniziale della forma, in pollici.|1|
|Larghezza iniziale|Larghezza iniziale della forma, espressa in pollici.|1.5|
|Esposizione del colore di riempimento come proprietà<br /><br /> Modalità sfumatura di riempimento esposta<br /><br /> Colore del contorno esposto come proprietà<br /><br /> Stile del trattino del contorno esposto come proprietà<br /><br /> Spessore del contorno esposto come proprietà<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà specificata di una forma. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla definizione della forma e **scegliere Aggiungi esposto.**|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<none>|
|Correzione del testo della descrizione comando|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida F1 per questa forma.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))