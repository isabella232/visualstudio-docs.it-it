---
title: Proprietà dei diagrammi
description: Informazioni sui diagrammi e su come è possibile impostare proprietà che specificano la modalità di visualizzazione dei diagrammi nella finestra di progettazione generata.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 55479e0882532249b89b36920023c83634ac7c21122078fbe6063fcb32dc2c58
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121288555"
---
# <a name="properties-of-diagrams"></a>Proprietà dei diagrammi
È possibile impostare proprietà che specificano la modalità di visualizzazione dei diagrammi nella finestra di progettazione generata. Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.

 Per altre informazioni, vedere [Come definire un linguaggio specifico di dominio.](../modeling/how-to-define-a-domain-specific-language.md) Per altre informazioni su come usare queste proprietà, vedere Personalizzare ed [estendere un linguaggio specifico di dominio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Nella tabella seguente sono elencate le proprietà dei diagrammi.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento|Colore di riempimento per il diagramma.|White|
|Colore del testo|Colore del testo visualizzato nel diagramma.|Nero|
|Modificatore di accesso|Modificatore di accesso della classe (public o internal).|Pubblico|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice generata.|\<none>|
|Genera un valore derivato da Double|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Eseguire l'override ed estendere le classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Eseguire l'override ed estendere le classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dal diagramma ( `none` `abstract` , o `sealed` ).|Nessuno|
|Diagramma di base|Classe di base di questo diagramma.|(nessuna)|
|Nome|Nome del diagramma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi associato a questo diagramma.|Spazio dei nomi corrente|
|Classe rappresentata|Classe di dominio radice rappresentata da questo diagramma.|Classe radice corrente, se applicabile|
|Note|Note informali associate a questo elemento.|\<none>|
|Espone il colore di riempimento come proprietà|Se `True` , l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generata. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla forma del diagramma e **scegliere Aggiungi esposto.**|Falso|
|Espone il colore del testo come proprietà|Se `True` , l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generata. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla forma del diagramma e **scegliere Aggiungi esposto.**|Falso|
|Descrizione|Descrizione utilizzata per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo diagramma.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida F1 per questo diagramma.|\<none>|

## <a name="see-also"></a>Vedi anche

[Glossario degli strumenti del linguaggio specifico di dominio](/previous-versions/bb126564(v=vs.100))