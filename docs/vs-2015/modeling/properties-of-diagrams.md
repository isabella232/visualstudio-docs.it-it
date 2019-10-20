---
title: Proprietà dei diagrammi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31fb06512457f919b67d41c3fb4096e4c3477426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652025"
---
# <a name="properties-of-diagrams"></a>Proprietà di diagrammi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile impostare proprietà che specificano il modo in cui i diagrammi verranno visualizzati nella finestra di progettazione generata. Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.

 Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Nella tabella seguente sono elencate le proprietà dei diagrammi.

|proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|Colore riempimento|Colore di riempimento per il diagramma.|bianco|
|Colore del testo|Colore del testo visualizzato nel diagramma.|Nero|
|Modificatore di accesso|Modificatore di accesso della classe (Public o Internal).|Public|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice generata.|\<nessuno>|
|Genera il doppio derivato|Se `True`, verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite sostituzioni). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Con costruttore personalizzato|Se `True`, nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dal diagramma (`none`, `abstract` o `sealed`).|Nessuno|
|Diagramma di base|Classe base del diagramma.|(nessuno)|
|Name|Nome del diagramma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questo diagramma.|Spazio dei nomi corrente|
|Classe rappresentata|Classe di dominio radice rappresentata da questo diagramma.|Classe radice corrente, se applicabile|
|Note|Note informali associate a questo elemento.|\<nessuno>|
|Espone il colore di riempimento come proprietà|Se `True`, l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generata. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **Aggiungi esplosa**.|False|
|Espone il colore del testo come proprietà|Se `True`, l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generata. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **Aggiungi esplosa**.|False|
|Descrizione|Descrizione utilizzata per documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo diagramma.|\<nessuno>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questo diagramma.|\<nessuno>|

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
