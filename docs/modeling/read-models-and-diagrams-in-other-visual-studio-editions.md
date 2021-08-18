---
title: Leggere modelli e diagrammi in altre edizioni di Visual Studio
description: Informazioni sulla lettura di modelli e diagrammi in Visual Studio, nonché sul comportamento di sola lettura quando si usa una versione di Visual Studio che non supporta la creazione di modelli.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4adcdb442e31a0de834a05a06ea96981b761ea73
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100777"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leggere modelli e diagrammi in altre edizioni di Visual Studio

Quando si apre un modello in una versione di Visual Studio che non supporta la creazione di modelli, il modello viene aperto in modalità di sola lettura. In questa modalità è possibile modificare il layout dei diagrammi, ma non modificare il modello.

Per informazioni su quali versioni di Visual Studio la creazione di modelli, vedere Supporto delle versioni per gli strumenti di [architettura e modellazione.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Accesso a un modello e ai diagrammi

Per leggere un diagramma delle dipendenze, è necessario innanzitutto usare Visual Studio per aprire il progetto di modellazione e quindi aprire il diagramma al suo interno.

Per questo motivo, se si vuole leggere un diagramma delle dipendenze, è necessario avere anche accesso al progetto di modellazione in cui è stato creato. È possibile eseguire questa operazione accedendo al progetto dal controllo del codice sorgente o ottenendo una copia dei file di progetto.

> [!NOTE]
> Non si applica alle mappe codice e ai diagrammi classi .NET generati dal codice. Questi diagrammi possono essere visualizzati indipendentemente dal progetto di modellazione.

Per leggere un diagramma delle dipendenze, il set minimo di file necessari è il seguente:

- I due file di diagramma per il diagramma da leggere, ad esempio **MyDiagram.classdiagram e MyDiagram.classdiagram.layout**.

    > [!NOTE]
    > Per i diagrammi delle dipendenze, è necessario avere anche il file denominato _MyDiagram_**.layerdiagram.suppressions**.

- File di progetto di modellazione (**MyModel.modelproj**)

- File del modello radice (**ModelDefinition\MyModel.uml**)

- File di pacchetto per qualsiasi pacchetto a cui si fa riferimento nel diagramma (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Modifiche eseguibili in modalità di sola lettura

Se si apre un modello e i relativi diagrammi in una versione di Visual Studio che non supporta la creazione di modelli, non sarà possibile modificare il modello. Non è possibile modificare gli elementi e le relazioni visualizzate nei diagrammi o in Esplora modelli. Tuttavia, è possibile apportare alcune modifiche al layout dei diagrammi:

- Ridisporre le forme e i connettori nel diagramma.

- Espandere e comprimere le forme.

Queste modifiche possono essere salvate. Se si desidera rendere le modifiche visibili ad altri utenti, è necessario inviare almeno i file **di layout** aggiornati.

## <a name="see-also"></a>Vedi anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)
