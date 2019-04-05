---
title: Riferimento API per SDK di modellazione
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1e788abb51425e0f2656c10ba860602a36c8aad8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969385"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Riferimento API per SDK di modellazione per Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione e Visual Studio Modeling SDK offre la piattaforma in cui vengono compilati gli strumenti UML e i linguaggi specifici di dominio (DSL).

> [!NOTE]
>  Per informazioni sull'API di modellazione UML, vedere [riferimento API per l'estendibilità di modellazione UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Per informazioni sulla trasformazione del testo, vedere [personalizzazione di trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md).

 In questa sezione contiene materiale di riferimento per gli spazi dei nomi con nomi che iniziano con "VisualStudio".

|Spazio dei nomi|Content|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classi, ad esempio ModelElement, ovvero la classe di base di tutte le classi di dominio definite in un linguaggio DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classi che fanno parte di una definizione DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Gli strumenti di misurazione del Visualizzatore di Store e le prestazioni del modello.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classi, ad esempio ShapeElement, ovvero la classe di base di tutte le forme definite in un linguaggio DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Metodi di azione e la selezione.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|L'API della finestra di progettazione di definizione DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classi interne della finestra di progettazione di definizione DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attributi che consentono di estendere la finestra di progettazione DSL con comandi, movimenti e convalida.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metodi di estensione per l'oggetto ModelElement che implementano l'estendibilità di linguaggio specifico di dominio.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Attributi di estendibilità|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Consente di rendere le parti di un modello di sola lettura.|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|L'API di Modelbus che consente di integrare modelli diversi.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|La finestra di dialogo che consente agli utenti di passare a modelli ed elementi per creare un riferimento Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Il servizio di selezione.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Framework di adattatore ModelBus per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|La finestra di dialogo di selezione che consente agli utenti di passare a modelli ed elementi per creare un riferimento Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|L'interfaccia tra DSL e [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|È possibile definire comandi di menu di scelta rapida (contestuale).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|È possibile definire vincoli di convalida.|

## <a name="see-also"></a>Vedere anche
 [Riferimento API per l'estensibilità di modellazione UML](../modeling/api-reference-for-uml-modeling-extensibility.md) [personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)
