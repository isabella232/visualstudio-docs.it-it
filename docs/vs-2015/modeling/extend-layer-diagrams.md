---
title: Estendere i diagrammi a livello Documenti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302336"
---
# <a name="extend-layer-diagrams"></a>Extend layer diagrams
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile scrivere codice per creare e aggiornare i diagrammi livello e per convalidare la struttura del codice programma in base ai diagrammi livello in Visual Studio. È possibile aggiungere comandi da visualizzare nel menu di scelta rapida (contestuale) dei diagrammi, personalizzare i movimenti di trascinamento della selezione e accedere al modello di livello dai modelli di testo. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) e distribuirle ad altri utenti di Visual Studio.

 Per altre informazioni sui diagrammi livello, vedere:

- [Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md)

- [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)

- [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)

- [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)

## <a name="requirements"></a><a name="prereqs"></a>Requisiti
 È necessario verificare che nel computer in cui si vogliono sviluppare le estensioni del livello sia installato quanto segue:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [SDK di modellazione per Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  È necessario avere installato una versione appropriata di Visual Studio nel computer in cui si vogliono eseguire le estensioni del livello. Per ulteriori informazioni, consultate [Distribuire un'estensione del modello](../modeling/deploy-a-layer-model-extension.md)di livello.

  Per individuare le versioni di Visual Studio che supportano i diagrammi livello, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>Contenuto della sezione
 [Aggiunta di comandi e movimenti a diagrammi livello](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Aggiungere strumenti di convalida dell'architettura personalizzati a diagrammi livello](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Aggiungere proprietà personalizzate ai diagrammi livello](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Esplorare e aggiornare i modelli di livello nel codice del programma](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Distribuire un'estensione del modello di livello](../modeling/deploy-a-layer-model-extension.md)

 [Risoluzione dei problemi relativi a estensioni per diagrammi livello](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Vedere anche
 [Definire e installare un'estensione](../modeling/define-and-install-a-modeling-extension.md) di modellazione Diagrammi livello: Diagrammi livello di riferimento: Linee guida Creare diagrammi livello dal codice Convalidare il codice con diagrammi livello [Generare file da un modello UML](../modeling/generate-files-from-a-uml-model.md) [Aprire un modello UML utilizzando l'API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md) di Visual StudioDefine a modelL [Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md) Create layer [diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md) Validate code with layer [diagrams](../modeling/validate-code-with-layer-diagrams.md) Generate files from a UML model Open a UML model by using the Visual Studio API
