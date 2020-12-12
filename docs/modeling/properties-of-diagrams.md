---
title: Proprietà dei diagrammi
description: Informazioni sui diagrammi e su come è possibile impostare le proprietà che specificano la modalità di visualizzazione dei diagrammi nella finestra di progettazione generata.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe27eb7dcfb8a984fceaee0700e1df44b6de4ef1
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361950"
---
# <a name="properties-of-diagrams"></a>Proprietà dei diagrammi
È possibile impostare proprietà che specificano il modo in cui i diagrammi verranno visualizzati nella finestra di progettazione generata. Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.

 Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Nella tabella seguente sono elencate le proprietà dei diagrammi.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento|Colore di riempimento per il diagramma.|bianco|
|Colore del testo|Colore del testo visualizzato nel diagramma.|Nero|
|Modificatore di accesso|Modificatore di accesso della classe (Public o Internal).|Pubblico|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice generata.|\<none>|
|Genera il doppio derivato|Se `True` , verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Con costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dal diagramma ( `none` , `abstract` o `sealed` ).|Nessuno|
|Diagramma di base|Classe base del diagramma.|(nessuna)|
|Nome|Nome del diagramma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questo diagramma.|Spazio dei nomi corrente|
|Classe rappresentata|Classe di dominio radice rappresentata da questo diagramma.|Classe radice corrente, se applicabile|
|Note|Note informali associate a questo elemento.|\<none>|
|Espone il colore di riempimento come proprietà|Se `True` , l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generata. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **Aggiungi esposti**.|Falso|
|Espone il colore del testo come proprietà|Se `True` , l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generata. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **Aggiungi esposti**.|Falso|
|Description|Descrizione utilizzata per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo diagramma.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questo diagramma.|\<none>|

## <a name="see-also"></a>Vedi anche

[Glossario degli strumenti del linguaggio specifico di dominio](/previous-versions/bb126564(v=vs.100))