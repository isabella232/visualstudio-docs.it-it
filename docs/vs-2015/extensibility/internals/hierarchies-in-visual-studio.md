---
title: Gerarchie
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22943d3049ff0e24d00c7c29750e7dcd0efaf846
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158367"
---
# <a name="hierarchies-in-visual-studio"></a>Gerarchie in Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE) Visualizza un progetto come *gerarchia*. Nell'IDE, una gerarchia è una struttura ad albero di nodi, in cui ogni nodo dispone di un set di proprietà associate. Una *gerarchia del progetto* è un contenitore che include gli elementi del progetto, le relazioni tra gli elementi e le proprietà e i comandi associati agli elementi.

 In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è possibile gestire le gerarchie di progetto utilizzando l'interfaccia della gerarchia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia reindirizza i comandi richiamati dagli elementi del progetto alla finestra della gerarchia appropriata anziché al gestore di comando standard.

## <a name="project-hierarchies"></a>Gerarchie di progetto
 Ogni gerarchia del progetto contiene elementi che è possibile visualizzare e modificare. Questi elementi variano a seconda del tipo di progetto. Un progetto di database, ad esempio, può contenere stored procedure, viste di database e tabelle di database. Un progetto in linguaggio di programmazione, d'altra parte, includerà probabilmente file di origine e file di risorse per le bitmap e le finestre di dialogo. Le gerarchie possono essere annidate, in modo da garantire una maggiore flessibilità durante la creazione di una gerarchia del progetto.

 Quando si crea un nuovo tipo di progetto, il tipo di progetto controlla il set completo di elementi che è possibile modificare al suo interno. Tuttavia, i progetti possono contenere elementi per i quali non è disponibile il supporto per la modifica. Ad esempio, i progetti Visual C++ possono contenere file HTML, anche se Visual C++ non fornisce alcun editor personalizzato per il tipo di file HTML.

 Le gerarchie gestiscono la persistenza degli elementi in essi contenuti. L'implementazione della gerarchia deve controllare eventuali proprietà speciali che influiscono sulla persistenza degli elementi all'interno della gerarchia. Se, ad esempio, gli elementi rappresentano oggetti in un repository anziché in file, l'implementazione della gerarchia deve controllare la persistenza di tali oggetti. L'IDE stesso indirizza la gerarchia per salvare gli elementi in conformità con l'input dell'utente, ma l'IDE non controlla le azioni necessarie per salvare tali elementi. Il progetto è invece sotto controllo.

 Quando un utente apre un elemento in un editor, la gerarchia che controlla tale elemento viene selezionata e diventa la gerarchia attiva. La gerarchia selezionata determina il set di comandi disponibili per agire sull'elemento. Il rilevamento dello stato attivo dell'utente in questo modo consente alla gerarchia di riflettere il contesto corrente dell'utente.

## <a name="see-also"></a>Vedere anche
 [Project Types](../../extensibility/internals/project-types.md) [Selezione dei tipi di progetto e valuta negli esempi di](../../extensibility/internals/selection-and-currency-in-the-ide.md) [VSSDK](../../misc/vssdk-samples.md) IDE
