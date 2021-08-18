---
title: Proprietà delle corsie
description: Informazioni su come le corsie dividono un diagramma in aree verticali o orizzontali e come è possibile definire altre forme da visualizzare all'interno delle corsie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 27df14cad337fcb1ce1dffaeab1d501a6ff549e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123580"
---
# <a name="properties-of-swimlanes"></a>Proprietà delle corsie
È possibile aggiungere corsie a un diagramma. Le corsie dividono un diagramma in aree verticali o orizzontali. È possibile definire altre forme da visualizzare all'interno delle corsie. Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione di [un Domain-Specific linguaggio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le corsie hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento corpo|Colore di riempimento per il corpo della corsia.|White|
|Colore riempimento intestazione|Colore di riempimento per l'intestazione della corsia.|grigio scuro|
|Colore separatore|Colore della linea di separazione.|Lightgray|
|Stile linea separatore|Stile della riga separatore ( `Solid` , , , , o `Dash` `Dot` `DashDot` `DashDotDot` `Custom` ).|`Dash`|
|Spessore separatore|Spessore della linea separatore in pollici.|0.03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa corsia.|Nero|
|Modificatore di accesso|Livello di accesso della classe ( `public` o `internal` ).|Pubblico|
|Attributi personalizzati|Usato per aggiungere attributi alla classe di codice generata da questa corsia.|\<none>|
|Genera una derivazione doppia|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dalla corsia ( `none` o `abstract` `sealed` ).|Nessuno|
|Corsia di base|Classe di base di questa corsia.|(nessuna)|
|Nome|Nome della corsia.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa corsia.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando ( `fixed` `variable` , o `none` ). Se `fixed` , viene usato il valore della proprietà ; se , la descrizione comando viene definita nel codice `Fixed Tooltip Text` `variable` personalizzato.|\<none>|
|Note|Note informali associate a questa corsia.|\<none>|
|Allineamento|Allineamento orizzontale o verticale.|Vertical|
|Altezza iniziale|Altezza iniziale della corsia, in pollici. Applicabile solo alle corsie orizzontali.|0|
|Larghezza iniziale|Larghezza iniziale della corsia, espressa in pollici. Applicabile solo alle corsie verticali.|0|
|Espone il colore del testo|Se `True` , l'utente può impostare il colore di una corsia nella finestra di progettazione generata. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla forma corsia e scegliere **Aggiungi esposto**.|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per fare riferimento a questa classe di corsia.|\<none>|
|Correzione del testo della descrizione comando|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave usata per indicizzare la Guida di F1 per questa corsia.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))