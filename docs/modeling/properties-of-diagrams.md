---
title: Proprietà dei diagrammi
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
ms.openlocfilehash: 762c2acb6774d7eb4949087fdd91e85c86acd6bb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595423"
---
# <a name="properties-of-diagrams"></a>Proprietà dei diagrammi
È possibile impostare proprietà che specificano il modo in cui i diagrammi verranno visualizzati nella finestra di progettazione generata. Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.

 Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Nella tabella seguente sono elencate le proprietà dei diagrammi.

|Gli|Descrizione|Default|
|-|-|-|
|Colore riempimento|Colore di riempimento per il diagramma.|Bianco|
|Colore del testo|Colore del testo visualizzato nel diagramma.|nero|
|Modificatore di accesso|Modificatore di accesso della classe (Public o Internal).|Public|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice generata.|\<nessuno>|
|Genera il doppio derivato|Se `True`, verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite sostituzioni). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Con costruttore personalizzato|Se `True`, nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dal diagramma (`none`, `abstract`o `sealed`).|nessuna|
|Diagramma di base|Classe base del diagramma.|(nessuno)|
|Name|Nome del diagramma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questo diagramma.|Spazio dei nomi corrente|
|Classe rappresentata|Classe di dominio radice rappresentata da questo diagramma.|Classe radice corrente, se applicabile|
|Note|Note informali associate a questo elemento.|\<nessuno>|
|Espone il colore di riempimento come proprietà|Se `True`, l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generata. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **Aggiungi esposti**.|Falso|
|Espone il colore del testo come proprietà|Se `True`, l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generata. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **Aggiungi esposti**.|Falso|
|Descrizione|Descrizione utilizzata per documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo diagramma.|\<nessuno>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questo diagramma.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

[Glossario degli strumenti del linguaggio specifico di dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
