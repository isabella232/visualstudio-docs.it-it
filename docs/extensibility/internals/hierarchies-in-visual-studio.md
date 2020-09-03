---
title: Gerarchie in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708193"
---
# <a name="hierarchies-in-visual-studio"></a>Gerarchie in Visual Studio
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) Visualizza un progetto come *gerarchia*. Nell'IDE, una gerarchia è una struttura ad albero di nodi, in cui ogni nodo dispone di un set di proprietà associate. Una *gerarchia del progetto* è un contenitore che include gli elementi del progetto, le relazioni tra gli elementi e le proprietà e i comandi associati agli elementi.

 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è possibile gestire le gerarchie di progetto utilizzando l'interfaccia della gerarchia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia reindirizza i comandi richiamati dagli elementi del progetto alla finestra della gerarchia appropriata anziché al gestore di comando standard.

## <a name="project-hierarchies"></a>Gerarchie di progetto
 Ogni gerarchia del progetto contiene elementi che è possibile visualizzare e modificare. Questi elementi variano a seconda del tipo di progetto. Un progetto di database, ad esempio, può contenere stored procedure, viste di database e tabelle di database. Un progetto in linguaggio di programmazione, d'altra parte, includerà probabilmente file di origine e file di risorse per le bitmap e le finestre di dialogo. Le gerarchie possono essere annidate, in modo da garantire una maggiore flessibilità durante la creazione di una gerarchia del progetto.

 Quando si crea un nuovo tipo di progetto, il tipo di progetto controlla il set completo di elementi che è possibile modificare al suo interno. Tuttavia, i progetti possono contenere elementi per i quali non è disponibile il supporto per la modifica. Ad esempio, i progetti Visual C++ possono contenere file HTML, anche se Visual C++ non fornisce alcun editor personalizzato per il tipo di file HTML.

 Le gerarchie gestiscono la persistenza degli elementi in essi contenuti. L'implementazione della gerarchia deve controllare eventuali proprietà speciali che influiscono sulla persistenza degli elementi all'interno della gerarchia. Se, ad esempio, gli elementi rappresentano oggetti in un repository anziché in file, l'implementazione della gerarchia deve controllare la persistenza di tali oggetti. L'IDE stesso indirizza la gerarchia per salvare gli elementi in conformità con l'input dell'utente, ma l'IDE non controlla le azioni necessarie per salvare tali elementi. Il progetto è invece sotto controllo.

 Quando un utente apre un elemento in un editor, la gerarchia che controlla tale elemento viene selezionata e diventa la gerarchia attiva. La gerarchia selezionata determina il set di comandi disponibili per agire sull'elemento. Il rilevamento dello stato attivo dell'utente in questo modo consente alla gerarchia di riflettere il contesto corrente dell'utente.

## <a name="see-also"></a>Vedere anche
- [Tipi di progetto](../../extensibility/internals/project-types.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
