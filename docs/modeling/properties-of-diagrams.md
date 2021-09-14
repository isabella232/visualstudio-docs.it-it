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
ms.openlocfilehash: 5128befb2460a364758a692cfe5cac0a30732f1e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637571"
---
# <a name="properties-of-diagrams"></a>Proprietà dei diagrammi
È possibile impostare proprietà che specificano la modalità di visualizzazione dei diagrammi nella finestra di progettazione generata. Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.

 Per altre informazioni, vedere [Come definire un linguaggio specifico di dominio.](../modeling/how-to-define-a-domain-specific-language.md) Per altre informazioni su come usare queste proprietà, vedere [Personalizzare ed estendere un linguaggio specifico di dominio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Nella tabella seguente sono elencate le proprietà dei diagrammi.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento|Colore di riempimento per il diagramma.|White|
|Colore del testo|Colore del testo visualizzato nel diagramma.|Nero|
|Modificatore di accesso|Modificatore di accesso della classe (pubblico o interno).|Pubblico|
|Attributi personalizzati|Usato per aggiungere attributi alla classe di codice generata.|\<none>|
|Genera una derivazione doppia|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Eseguire l'override ed estendere le classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Eseguire l'override ed estendere le classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dal diagramma ( `none` , `abstract` o `sealed` ).|Nessuno|
|Diagramma di base|Classe di base di questo diagramma.|(nessuna)|
|Nome|Nome del diagramma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questo diagramma.|Spazio dei nomi corrente|
|Classe rappresentata|Classe di dominio radice rappresentata da questo diagramma.|Classe radice corrente, se applicabile|
|Note|Note informali associate a questo elemento.|\<none>|
|Espone la proprietà Fill Color As|Se `True` , l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generata. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **Aggiungi esposto**.|Falso|
|Espone la proprietà Text Color As|Se `True` , l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generata. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **Aggiungi esposto**.|Falso|
|Descrizione|Descrizione utilizzata per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo diagramma.|\<none>|
|Parola chiave della Guida|Parola chiave usata per indicizzare la Guida di F1 per questo diagramma.|\<none>|

## <a name="see-also"></a>Vedi anche

[Glossario degli strumenti del linguaggio specifico di dominio](/previous-versions/bb126564(v=vs.100))