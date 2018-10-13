---
title: Leggere modelli e diagrammi in altre edizioni di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: e38514b2c65fb5db557d49b1ae2a7daf0b932dd9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277862"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leggere modelli e diagrammi in altre edizioni di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si apre un modello in una versione di Visual Studio che non supporta la creazione di modelli, il modello viene aperto in modalità di sola lettura. In questa modalità è possibile modificare il layout dei diagrammi, ma non modificare il modello.  
  
 Per le versioni di Visual Studio che supportano la creazione di modelli, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Accesso a un modello e ai diagrammi  
 Per leggere un diagramma UML o un diagramma livello, è necessario usare prima Visual Studio per aprire il progetto di modellazione e quindi aprire il diagramma in esso contenuti.  
  
 Per questo motivo, se si vuole leggere un diagramma UML o un diagramma livello, è necessario avere accesso anche al progetto di modellazione nel quale è stato creato. Per eseguire questa operazione, è possibile accedere al progetto da [!INCLUDE[esprscc](../includes/esprscc-md.md)] oppure ottenere una copia dei file di progetto.  
  
> [!NOTE]
>  Non si applica alle mappe codice e ai diagrammi classi .NET generati dal codice. Questi diagrammi possono essere visualizzati indipendentemente dal progetto di modellazione.  
  
 Per leggere un diagramma UML o un diagramma livello, è necessario almeno il set di file seguente:  
  
-   I due file diagramma per il diagramma da leggere, ad esempio, **MyDiagram.classdiagram e MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Per i diagrammi livello, è necessario anche il file denominato _MyDiagram_**. MyDiagram**.  
  
-   File di progetto di modellazione (**MyModel. modelproj**)  
  
-   Il file del modello radice (**ModelDefinition\MyModel.uml**)  
  
-   I file del pacchetto per i pacchetti di cui viene fatto riferimento nel diagramma (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Modifiche eseguibili in modalità di sola lettura  
 Se si apre un modello e i relativi diagrammi in una versione di Visual Studio che non supporta la creazione di modelli, non sarà possibile modificare il modello. Non è possibile modificare gli elementi e le relazioni visualizzate nei diagrammi o in Esplora modelli. Tuttavia, è possibile apportare alcune modifiche al layout dei diagrammi:  
  
-   Ridisporre le forme e i connettori nel diagramma.  
  
-   Espandere e comprimere le forme.  
  
 Queste modifiche possono essere salvate. Se si desidera rendere visibili ad altri utenti le modifiche, è necessario inviare almeno aggiornato **layout** file.  
  
##  <a name="RelatedTopics"></a> Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md)|Un diagramma livello mostra la struttura di un'architettura esistente o proposta. Dopo la scrittura del codice, è possibile convalidarlo automaticamente in base a un diagramma livello.|  
|[Diagrammi di attività UML: riferimento](../modeling/uml-activity-diagrams-reference.md)|Un diagramma di attività mostra un flusso di lavoro in un processo aziendale o nel software.|  
|[Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)|Un diagramma classi mostra tipi e relazioni usati in molti contesti, ad esempio codice, schemi di database, protocolli di comunicazione o il glossario dei termini usati per descrivere un dominio aziendale.|  
|[Diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md)|Un diagramma dei componenti mostra le parti separabili in una progettazione software e le relative interfacce.|  
|[Diagrammi di sequenza UML: riferimenti](../modeling/uml-sequence-diagrams-reference.md)|Un diagramma di sequenza mostra le interazioni tra elementi in una progettazione software.|  
|[Diagrammi casi d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md)|Un diagramma caso di utilizzo mostra gli utenti di un sistema e le attività che possono eseguire per realizzare obiettivi specifici.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)



