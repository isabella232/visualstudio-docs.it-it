---
title: Informazioni di riferimento sulle API per l'SDK di modellazione
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3915dc0ee7359c8fb0093f397542afb557d0796a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654329"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Riferimento API per SDK di modellazione per Visual Studio

Visual Studio Visualization and Modeling SDK fornisce la piattaforma in cui vengono compilati gli strumenti di linguaggio specifico di dominio (DSL).

Questa sezione contiene materiale di riferimento per gli spazi dei nomi con nomi che iniziano con "Microsoft. VisualStudio. Modeling".

|Spazio dei nomi|Contenuto|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classi come ModelElement, che è la classe di base di tutte le classi di dominio definite in un linguaggio DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classi che fanno parte di una definizione DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Il visualizzatore del negozio di modelli e gli strumenti di misurazione delle prestazioni.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classi come ShapeElement, che è la classe di base di tutte le forme definite in un linguaggio DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Metodi di movimento e selezione.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|API della finestra di progettazione delle definizioni DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classi interne della finestra di progettazione delle definizioni DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attributi che consentono di estendere la finestra di progettazione DSL con comandi, movimenti e convalida.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metodi di estensione per ModelElement che implementano l'estensibilità DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Attributi di estendibilità|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Consente di rendere di sola lettura parti di un modello.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|API ModelBus, che consente di integrare modelli diversi.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|La finestra di dialogo che consente agli utenti di passare a modelli ed elementi per creare riferimenti ModelBus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Il servizio di selezione.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Framework Adapter ModelBus per Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|La finestra di dialogo di selezione che consente agli utenti di passare a modelli ed elementi per creare riferimenti ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfaccia tra DSLs e Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Consente di definire i comandi di menu di scelta rapida.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Consente di definire vincoli di convalida.|

## <a name="see-also"></a>Vedere anche

- [Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)
