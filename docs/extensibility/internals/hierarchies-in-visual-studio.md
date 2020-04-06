---
title: 'Gerarchie in Visual Studio: Documenti Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708193"
---
# <a name="hierarchies-in-visual-studio"></a>Gerarchie in Visual Studio
L'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE) visualizza un progetto come *una gerarchia*. Nell'IDE, una gerarchia è una struttura ad albero di nodi, in cui ogni nodo dispone di un set di proprietà associate. Una *gerarchia* di progetto è un contenitore che contiene gli elementi del progetto, le relazioni degli elementi e le proprietà e i comandi associati degli elementi.

 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è possibile gestire le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>gerarchie di progetto utilizzando l'interfaccia della gerarchia, . L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> reindirizza i comandi richiamati dagli elementi di progetto alla finestra della gerarchia appropriata anziché al gestore di comando standard.

## <a name="project-hierarchies"></a>Gerarchie di progetto
 Ogni gerarchia di progetto contiene elementi che è possibile visualizzare e modificare. Questi elementi variano a seconda del tipo di progetto. Ad esempio, un progetto di database potrebbe contenere stored procedure, viste di database e tabelle di database. Un progetto in linguaggio di programmazione, d'altra parte, includerà probabilmente i file di origine e i file di risorse per le bitmap e le finestre di dialogo. Le gerarchie possono essere annidate, con una maggiore flessibilità quando si crea una gerarchia di progetto.

 Quando si crea un nuovo tipo di progetto, il tipo di progetto controlla l'insieme completo di elementi che possono essere modificati in esso. Tuttavia, i progetti possono contenere elementi per i quali non dispongono del supporto per la modifica. Ad esempio, i progetti di Visual Cè possono contenere file HTML, anche se in Visual Cè non è stato fornito alcun editor personalizzato per il tipo di file HTML.

 Le gerarchie gestiscono la persistenza degli elementi in essi contenuti. L'implementazione della gerarchia deve controllare tutte le proprietà speciali che influiscono sulla persistenza degli elementi all'interno della gerarchia. Ad esempio, se gli elementi rappresentano oggetti in un repository anziché file, l'implementazione della gerarchia deve controllare la persistenza di tali oggetti. L'IDE stesso indica alla gerarchia per salvare gli elementi in conformità con l'input dell'utente, ma l'IDE non controlla le azioni necessarie per salvare tali elementi. Al contrario, il progetto è in controllo.

 Quando un utente apre un elemento in un editor, la gerarchia che controlla tale elemento viene selezionato e diventa la gerarchia attiva. La gerarchia selezionata determina il set di comandi disponibili per agire sull'elemento. Il rilevamento dello stato attivo dell'utente in questo modo consente alla gerarchia di riflettere il contesto corrente dell'utente.

## <a name="see-also"></a>Vedere anche
- [Tipi di progetto](../../extensibility/internals/project-types.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
