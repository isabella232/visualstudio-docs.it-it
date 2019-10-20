---
title: Leggere modelli e diagrammi in altre edizioni di Visual Studio
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33ae88358d77ac7c70a74cecb879eef3c4ca8b8c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658116"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leggere modelli e diagrammi in altre edizioni di Visual Studio

Quando si apre un modello in una versione di Visual Studio che non supporta la creazione di modelli, il modello viene aperto in modalità di sola lettura. In questa modalità è possibile modificare il layout dei diagrammi, ma non modificare il modello.

Per informazioni sulle versioni di Visual Studio che supportano la creazione del modello, vedere [supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Accesso a un modello e ai diagrammi

Per leggere un diagramma delle dipendenze, è necessario innanzitutto utilizzare Visual Studio per aprire il progetto di modello e quindi aprire il diagramma al suo interno.

Per questo motivo, se si desidera leggere un diagramma delle dipendenze, è inoltre necessario disporre dell'accesso al progetto di modello in cui è stato creato. Questa operazione può essere eseguita accedendo al progetto dal controllo del codice sorgente o ottenendo una copia dei file di progetto.

> [!NOTE]
> Non si applica alle mappe codice e ai diagrammi classi .NET generati dal codice. Questi diagrammi possono essere visualizzati indipendentemente dal progetto di modellazione.

Per leggere un diagramma delle dipendenze, il set minimo di file necessario è il seguente:

- I due file di diagramma per il diagramma che si desidera leggere, ad esempio, **Diagram. classdiagram e Diagram. classdiagram. layout**.

    > [!NOTE]
    > Per i diagrammi di dipendenza, è necessario disporre anche del file denominato _Diagram_ **. layerdiagram.** requests.

- File di progetto di modello (**modelproj**)

- Il file del modello radice (**ModelDefinition\MyModel.Uml**)

- File del pacchetto per tutti i pacchetti a cui si fa riferimento nel diagramma (**ModelDefinition\MyPackage.Uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Modifiche eseguibili in modalità di sola lettura

Se si apre un modello e i relativi diagrammi in una versione di Visual Studio che non supporta la creazione di modelli, non sarà possibile modificare il modello. Non è possibile modificare gli elementi e le relazioni visualizzate nei diagrammi o in Esplora modelli. Tuttavia, è possibile apportare alcune modifiche al layout dei diagrammi:

- Ridisporre le forme e i connettori nel diagramma.

- Espandere e comprimere le forme.

Queste modifiche possono essere salvate. Se si desidera rendere le modifiche visibili ad altri utenti, è necessario inviare almeno i file con **estensione layout** aggiornati.

## <a name="see-also"></a>Vedere anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)