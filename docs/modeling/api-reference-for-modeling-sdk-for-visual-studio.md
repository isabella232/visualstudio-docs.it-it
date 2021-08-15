---
title: Informazioni di riferimento sulle API per Modeling SDK
description: Informazioni su come Visual Studio Visualization and Modeling SDK fornisce la piattaforma in cui vengono compilati gli strumenti DSL (Domain Specific Languages).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 5674486ec330dc804fa43836f64dcc439e0fc4a169244db217a41fe4cecd193c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316916"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Riferimento API per SDK di modellazione per Visual Studio

L Visual Studio Sdk di visualizzazione e modellazione fornisce la piattaforma su cui vengono compilati gli strumenti DSL (Domain Specific Languages).

Questa sezione contiene materiale di riferimento per gli spazi dei nomi con nomi che iniziano con "Microsoft.VisualStudio.Modeling".

|Spazio dei nomi|Content|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classi come ModelElement, che è la classe di base di tutte le classi di dominio definite in un DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classi che fanno parte di una definizione DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Visualizzatore archivio modelli e strumenti di misurazione delle prestazioni.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classi come ShapeElement, che è la classe di base di tutte le forme definite in un DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Metodi Gesture e Selection.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|API di Progettazione definizioni DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classi interne di Progettazione definizioni DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attributi che consentono di estendere la finestra di progettazione DSL con comandi, movimenti e convalida.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metodi di estensione per ModelElement che implementano l'estendibilità DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Attributi di estendibilità|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Consente di rendere parti di un modello di sola lettura.|
|[Microsoft.VisualStudio.Modeling.Integration](/previous-versions/ee904412(v=vs.140))|L'API Modelbus, che consente di integrare modelli diversi.|
|[Microsoft.VisualStudio.Modeling.Integration.Picker](/previous-versions/ee904394(v=vs.140))|Finestra di dialogo che consente agli utenti di passare a modelli ed elementi per creare riferimenti modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Servizio di selezione.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell](/previous-versions/ee869435(v=vs.140))|Framework dell'adapter modelbus per Visual Studio.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell.Picker](/previous-versions/ee886769(v=vs.140))|Finestra di dialogo Selezione che consente agli utenti di passare a modelli ed elementi per creare riferimenti modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfaccia tra DSLs e Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Consente di definire i comandi di menu di scelta rapida.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Consente di definire vincoli di convalida.|

## <a name="see-also"></a>Vedi anche

- [Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)
