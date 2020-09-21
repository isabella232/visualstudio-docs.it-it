---
title: Proprietà delle corsie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec27b9b4f90b1f3ec75edef6dca01b1ed7b8adf
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90807846"
---
# <a name="properties-of-swimlanes"></a>Proprietà delle corsie
È possibile aggiungere corsie a un diagramma. Le corsie dividono un diagramma in aree verticali o orizzontali. È possibile definire altre forme da visualizzare all'interno delle corsie. Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le corsie hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento corpo|Colore di riempimento per il corpo della corsia.|White|
|Colore riempimento intestazione|Colore di riempimento per l'intestazione della corsia.|grigio scuro|
|Colore separatore|Colore della linea di separazione.|LightGray|
|Stile linea separatore|Stile della linea di separazione ( `Solid` ,, `Dash` `Dot` , `DashDot` , `DashDotDot` o `Custom` ).|`Dash`|
|Spessore separatore|Spessore in pollici della linea del separatore.|0,03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa corsia.|Black|
|Modificatore di accesso|Livello di accesso della classe ( `public` o `internal` ).|Pubblico|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice generata da questa corsia.|\<none>|
|Genera il doppio derivato|Se `True` , verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite override). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Con costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla corsia ( `none` , `abstract` o `sealed` ).|Nessuno|
|Corsia di base|Classe di base di questa corsia.|(nessuna)|
|nome|Nome di questa corsia.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi affiliato a questa corsia.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando ( `fixed` , `variable` o `none` ). Se `fixed` , viene usato il valore della `Fixed Tooltip Text` proprietà; se `variable` , la descrizione comando è definita nel codice personalizzato.|\<none>|
|Note|Note informali associate a questa corsia.|\<none>|
|Allineamento|Allineamento orizzontale o verticale.|Vertical|
|Altezza iniziale|Altezza iniziale della corsia, in pollici. Applicabile solo alle corsie orizzontali.|0|
|Larghezza iniziale|Larghezza iniziale della corsia, in pollici. Applicabile solo alle corsie verticali.|0|
|Espone il colore del testo|Se `True` , l'utente può impostare il colore di una corsia nella finestra di progettazione generata. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla forma corsia e scegliere **Aggiungi esposti**.|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per fare riferimento a questa classe di corsia.|\<none>|
|Testo della descrizione comando fisso|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questa corsia.|\<none>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))