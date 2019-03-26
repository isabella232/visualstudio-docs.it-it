---
title: Estendere i diagrammi delle dipendenze
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 150621514f9153b1e9d67f8e9c85a00275c27b15
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416110"
---
# <a name="extend-dependency-diagrams"></a>Estendere i diagrammi delle dipendenze

È possibile scrivere codice per creare e aggiornare i diagrammi delle dipendenze e per convalidare la struttura del codice programma in base ai diagrammi delle dipendenze in Visual Studio. È possibile aggiungere comandi da visualizzare nel menu di scelta rapida (contestuale) dei diagrammi, personalizzare i movimenti di trascinamento della selezione e accedere al modello di livello dai modelli di testo. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) e distribuirle ad altri utenti di Visual Studio.

 Per altre informazioni sui diagrammi delle dipendenze, vedere:

-   [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)

-   [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)

-   [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)

-   [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

##  <a name="prereqs"></a> Requisiti

È necessario verificare che nel computer in cui si vogliono sviluppare le estensioni del livello sia installato quanto segue:

-   Visual Studio

-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

-   Modeling SDK per Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

È necessario avere installato una versione appropriata di Visual Studio nel computer in cui si vogliono eseguire le estensioni del livello.

Per le versioni di Visual Studio che supportano i diagrammi delle dipendenze, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>In questa sezione
 [Aggiungere comandi e movimenti ai diagrammi delle dipendenze](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Aggiungere strumenti di convalida dell'architettura personalizzati ai diagrammi delle dipendenze](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Aggiungere proprietà personalizzate ai diagrammi delle dipendenze](../modeling/add-custom-properties-to-layer-diagrams.md)

## <a name="see-also"></a>Vedere anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)
