---
title: Proprietà di diagrammi
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05c348edfa4665b138ac0f6069b0afaf6735da7a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937358"
---
# <a name="properties-of-diagrams"></a>Proprietà di diagrammi
È possibile impostare le proprietà che specificano come diagrammi apparirà nella finestra di progettazione generata. Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.

 Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Nella tabella seguente sono elencate le proprietà dei diagrammi.

|Proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Colore riempimento|Il colore di riempimento per il diagramma.|Bianco|
|Colore del testo|Colore del testo che viene visualizzato nel diagramma.|Nero|
|Modificatore di accesso|Il modificatore di accesso della classe (pubblico o interno).|Public|
|Attributi personalizzati|Consente di aggiungere attributi alla classe del codice generato.|\<nessuno>|
|Genera l'errore doppia derivati|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [sostituzione ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [sostituzione ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dal diagramma (`none`, `abstract`, o `sealed`).|nessuno|
|Diagramma di base|Classe di base di questo diagramma.|(nessuno)|
|nome|Il nome di questo diagramma.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi che è associato a questo diagramma.|Spazio dei nomi corrente|
|Classe rappresentata|La classe di dominio radice che rappresenta questo diagramma.|Classe radice corrente se applicabile|
|Note|Note informali associate a questo elemento.|\<nessuno>|
|Colore di riempimento esposte come proprietà|Se `True`, l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generata. Per impostare questa proprietà, fare doppio clic la forma di diagramma e fare clic su **Aggiungi esposta**.|False|
|Espone il colore del testo come proprietà|Se `True`, l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generata. Per impostare questa proprietà, fare doppio clic la forma di diagramma e fare clic su **Aggiungi esposta**.|False|
|Descrizione|La descrizione che consente di documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per il diagramma.|\<nessuno>|
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida F1 per questo diagramma.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

[Glossario sugli strumenti di linguaggio specifico di dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
