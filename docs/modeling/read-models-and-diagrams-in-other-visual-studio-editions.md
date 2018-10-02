---
title: Leggere modelli e diagrammi in altre edizioni di Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: cfd6188bc4d48f26e85ae8778d75d2fa99ef0f25
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859679"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leggere modelli e diagrammi in altre edizioni di Visual Studio
Quando si apre un modello in una versione di Visual Studio che non supporta la creazione di modelli, il modello viene aperto in modalità di sola lettura. In questa modalità è possibile modificare il layout dei diagrammi, ma non modificare il modello.

 Per le versioni di Visual Studio che supportano la creazione di modelli, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Accesso a un modello e ai diagrammi
 Per leggere un diagramma delle dipendenze, è necessario usare prima Visual Studio per aprire il progetto di modellazione e quindi aprire il diagramma in esso contenuti.

 Per questo motivo, se si vuole leggere un diagramma delle dipendenze, è anche necessario avere accesso al progetto di modellazione in cui è stato creato. È possibile farlo oppure accedere al progetto dal controllo del codice sorgente, ottenendo una copia dei file di progetto.

> [!NOTE]
>  Non si applica alle mappe codice e ai diagrammi classi .NET generati dal codice. Questi diagrammi possono essere visualizzati indipendentemente dal progetto di modellazione.

 Per leggere un diagramma delle dipendenze, il set minimo di file che devono essere è come segue:

-   I due file diagramma per il diagramma da leggere, ad esempio, **MyDiagram.classdiagram e MyDiagram.classdiagram.layout**.

    > [!NOTE]
    >  Per i diagrammi delle dipendenze, è necessario anche il file denominato _MyDiagram_**. MyDiagram**.

-   File di progetto di modellazione (**MyModel. modelproj**)

-   Il file del modello radice (**ModelDefinition\MyModel.uml**)

-   I file del pacchetto per i pacchetti di cui viene fatto riferimento nel diagramma (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Modifiche eseguibili in modalità di sola lettura
 Se si apre un modello e i relativi diagrammi in una versione di Visual Studio che non supporta la creazione di modelli, non sarà possibile modificare il modello. Non è possibile modificare gli elementi e le relazioni visualizzate nei diagrammi o in Esplora modelli. Tuttavia, è possibile apportare alcune modifiche al layout dei diagrammi:

-   Ridisporre le forme e i connettori nel diagramma.

-   Espandere e comprimere le forme.

 Queste modifiche possono essere salvate. Se si desidera rendere visibili ad altri utenti le modifiche, è necessario inviare almeno aggiornato **layout** file.

## <a name="RelatedTopics"></a> Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)|Un diagramma livello mostra la struttura di un'architettura esistente o proposta. Dopo la scrittura del codice, è possibile convalidarlo automaticamente in base a un diagramma livello.|

## <a name="see-also"></a>Vedere anche

- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)